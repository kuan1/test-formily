<template>
  <FormProvider :form="form">
    <ObjectField name="data">
      <template #default="{ field }">
        <div
          v-for="key in Object.keys(field.value || {})"
          :key="key"
          :style="{ marginBottom: '10px' }"
        >
          <Space>
            <Field :name="key" :component="[Input, { placeholder: key }]" />
            <Button @click="field.removeProperty(key)"> 删除 </Button>
          </Space>
        </div>
        <Space>
          <Field
            name="propertyName"
            basePath=""
            required
            :component="[Input, { placeholder: 'Property Name' }]"
          />
          <Button @click="addPropertyToField(field)"> 添加 </Button>
          <Button type="primary" @click="submit()"> 提交 </Button>
        </Space>
      </template>
    </ObjectField>
  </FormProvider>
</template>

<script lang="tsx" setup>
import { Input, Space, Button } from 'ant-design-vue'
import { createForm, ObjectField as F } from '@formily/core'
import { FormProvider, ObjectField, Field } from '@formily/vue'

const form = createForm()

const addPropertyToField = (field: F) => {
  const name = form.values.propertyName
  if (name && !form.existValuesIn(`data.${name}`)) {
    field.addProperty(name, '')
    form.deleteValuesIn('propertyName')
  }
}

const submit = async () => {
  const res = await form.submit()
  console.log(res)
}

</script>

<style>
</style>
