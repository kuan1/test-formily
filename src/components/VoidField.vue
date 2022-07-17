<template>
  <FormProvider :form="form">
    <Space>
      <VoidField name="layout">
        <Field name="name" :component="[Input]" />
      </VoidField>
      <FormConsumer>
        <template #default="{ form }">
          <Space>
            <Button
              @click="
                () => {
                  form
                    .query('layout')
                    .take()
                    .setState((state:any) => {
                      state.visible = !state.visible
                    })
                }
              "
            >
              {{ form.query('layout').get('visible') ? 'Hide' : 'Show' }}
            </Button>
            <Button type="primary" @click="() => form.submit().then((res:any) => { data = res})">提交</Button>
            <div>{{ JSON.stringify(form.values, null, 2) }}</div>

            <div>{{data}}</div>
          </Space>
        </template>
      </FormConsumer>
    </Space>
  </FormProvider>
</template>

<script lang="tsx" setup>
import { ref } from 'vue'
import { Input, Space, Button } from 'ant-design-vue'
import { createForm } from '@formily/core'
import { FormProvider, Field, FormConsumer, VoidField } from '@formily/vue'

const form = createForm()

const data = ref<any>({})

</script>

<style>
</style>
