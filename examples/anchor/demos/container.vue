<template>
  <div :id="`${path}#container`" class="anchor-demo anchor-container-demo">
    <t-anchor :id="`${path}#default`" container="#anchor-container">
      <t-anchor-item :href="`#${path}#content-1`" title="content-1" />
      <t-anchor-item :href="`#${path}#content-2`" title="content-2" />
      <t-anchor-item :href="`#${path}#content-3`" title="content-3" />
      <t-anchor-item :href="`#${path}#content-4`" title="content-4" />
    </t-anchor>
    <div id="anchor-container">
      <div :id="`${path}#content-1`" class="anchor-content-1">anchor-content-1</div>
      <div :id="`${path}#content-2`" class="anchor-content-2">anchor-content-2</div>
      <div :id="`${path}#content-3`" class="anchor-content-3">anchor-content-3</div>
      <div :id="`${path}#content-4`" class="anchor-content-4">anchor-content-4</div>
      <div :id="`${path}#content-5`" class="anchor-content-5">anchor-content-5</div>
    </div>
  </div>
</template>
<script setup>
import { computed, getCurrentInstance } from 'vue';
import get from 'lodash/get';

const { ctx } = getCurrentInstance();
const path = computed(() => get(ctx, '$route.path', ''));
</script>
<style lang="less" scoped>
.anchor-container-demo {
  display: flex;
}
#anchor-container {
  flex-grow: 1;
  height: 200px;
  overflow: auto;
  > div {
    text-align: center;
    font-size: 22px;
    line-height: 100px;
  }
  .anchor-content-1 {
    background: #ecf2fe;
  }
  .anchor-content-2 {
    background: #d4e3fc;
  }
  .anchor-content-3 {
    background: #bbd3fb;
  }
  .anchor-content-4 {
    background: #96bbf8;
  }
  .anchor-content-5 {
    background: #699ef5;
  }
}
</style>
