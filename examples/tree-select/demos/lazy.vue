<template>
  <div class="tdesign-tree-select-lazy">
    <t-tree-select
      v-model="value"
      :data="options"
      clearable
      placeholder="请选择"
      :tree-props="{
        load: loadFunc,
      }"
    />
  </div>
</template>
<script setup>
import { ref } from 'vue';

const options = [
  {
    label: '1',
    value: '1',
    children: true,
  },
  {
    label: '2',
    value: '2',
    children: true,
  },
];

const value = ref('');

const loadFunc = (node) =>
  new Promise((resolve) => {
    let timer = setTimeout(() => {
      let nodes = [];
      if (node.level < 2) {
        nodes = [
          {
            label: `${node.label}.1`,
            value: `${node.value}.1`,
            children: true,
          },
          {
            label: `${node.label}.2`,
            value: `${node.value}.2`,
            children: true,
          },
        ];
      }
      resolve(nodes);
      clearTimeout(timer);
      timer = null;
    }, 1000);
  });
</script>
<style scoped>
.tdesign-tree-select-lazy {
  width: 300px;
  margin: 0 20px;
}
</style>
