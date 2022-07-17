<template>
  <FormProvider :form="form">
    <ArrayField name="list">
      <template #default="{ field }">
        <div
          v-for="(item, index) in field.value || []"
          :key="item.id"
          :style="{ marginBottom: '10px' }"
        >
          <Space>
            <Field :name="`${index}.value`" :component="[Input]" />
            <Button
              @click="
                () => {
                  field.remove(index)
                }
              "
            >
              Remove
            </Button>
            <Button
              @click="
                () => {
                  field.moveUp(index)
                }
              "
            >
              Move Up
            </Button>
            <Button
              @click="
                () => {
                  field.moveDown(index)
                }
              "
            >
              Move Down
            </Button>
          </Space>
        </div>
        <Space>
          <Button @click="() => field.push({ id: Date.now(), value: '' })">
            添加
          </Button>
          <Button type="primary" @click="submit">
            提交
          </Button>
        </Space>
      </template>
    </ArrayField>
  </FormProvider>
</template>

<script lang="tsx" setup>
import { Input, Space, Button } from 'ant-design-vue'
import { createForm } from '@formily/core'
import { FormProvider, ArrayField, Field } from '@formily/vue'

const form = createForm()

const submit = async () => {
  const res = await form.submit()
  console.log(res)
}

</script>

<style>
</style>
