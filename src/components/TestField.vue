<template>
 <FormProvider :form="form">
  <a-space>
    <Field name="name" :component="[Input, { placeholder: '请输入名称' }]" />
    <Field name="age" :component="[Input, { placeholder: '请输入年龄' }]" />
    <a-button @click="test">修改</a-button>
    <a-button type="primary" @click="submit">提交</a-button>
  </a-space>
</FormProvider>
</template>

<script lang="tsx" setup>
import { createForm } from '@formily/core'
import { FormProvider, Field } from '@formily/vue'

import { Input } from 'ant-design-vue'

const form = createForm({
  initialValues: {name: '', age: 20}
})


const test = () => {
  form.setValues({
    name: '小明',
  })
}

const submit = async () => {
  const res = await form.submit()
  console.log(res)
}

</script>

<style>
</style>
