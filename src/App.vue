
<template>
  <a-card v-for="(is, key) in components" :key="key" :title="key" class="card">
    <component :is="is" />
  </a-card>
</template>

<script setup lang="ts">
import TestField from './components/TestField.vue';
import TestArrayField from './components/TestArrayField.vue';
import TestObjectField from './components/TestObjectField.vue';
import VoidField from './components/VoidField.vue';
import TestSchemaField from './components/TestSchemaField.vue';
import TestObserver from './components/TestObserver.vue';
import TestMapProps from './components/TestMapProps.vue';

const components = {
  TestField,
  TestArrayField,
  TestObjectField,
  VoidField,
  TestSchemaField,
  TestObserver,
  TestMapProps
}

</script>

<style scoped>
.card {
  margin: 1em;
}
</style>