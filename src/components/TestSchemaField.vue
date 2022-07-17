<template>
<FormProvider :form="form">
  <a-space>
    <SchemaField :schema="schema" />
    <a-button type="primary" @click="submit">提交</a-button>
  </a-space>
</FormProvider>
</template>

<script lang="tsx" setup>
import { Input } from 'ant-design-vue'
import { createForm } from '@formily/core'
import { FormProvider, createSchemaField, ISchema } from '@formily/vue'

const validator = (value:string) => {
  if (value.length > 10) {
    throw new Error('文字过长了')
  }
}

const { SchemaField } = createSchemaField({
  components: {
    Input,
  },
  scope: {
    validator
  }
})

const form = createForm()

const schema:ISchema = {
  type: 'object',
  properties: {
    input: {
      type: 'string',
      'x-component': 'Input',
      'x-disabled': true,
      'x-validator': {
        triggerType: 'onBlur',
        required: true,
        validator: '{{validator}}'
      },
      required: true,
    },
  },
}

const submit = async () => {
  const res = await form.submit()
  console.log(res)
}
</script>

<style>
</style>
