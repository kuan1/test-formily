
<template>
  <a-card v-for="item in components" :key="item.key" :title="item.key" class="card">
    <component :is="item.is" />
  </a-card>
</template>

<script setup lang="ts">
import TestField from './components/TestField.vue';
import TestArrayField from './components/TestArrayField.vue';
import TestObjectField from './components/TestObjectField.vue';
import VoidField from './components/VoidField.vue';
import TestSchemaField from './components/TestSchemaField.vue';

const components = [
  { is: TestField, key: 'TestField' },
  { is: TestArrayField, key: 'TestArrayField' },
  { is: TestObjectField, key: 'TestObjectField' },
  { is: VoidField, key: 'VoidField' },
  { is: TestSchemaField, key: 'TestSchemaField' },
]

</script>

<style scoped>
.card {
  margin: 1em;
}
</style>