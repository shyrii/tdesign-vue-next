<template>
  <t-menu theme="light" default-value="2-1" :collapsed="collapsed" height="550px">
    <template #logo>
      <span>LOGO</span>
    </template>
    <t-menu-item value="item1">
      <template #icon>
        <t-icon name="dashboard" />
      </template>
      仪表盘1
    </t-menu-item>
    <t-submenu value="2" mode="popup">
      <template #icon>
        <t-icon name="mail" />
      </template>
      <template #title>
        <span>信息区</span>
      </template>
      <t-menu-item value="2-1"> 菜单内容一 </t-menu-item>
      <t-menu-item value="2-2"> 菜单内容二 </t-menu-item>
      <t-menu-item value="2-3"> 菜单内容三 </t-menu-item>
    </t-submenu>
    <t-menu-item value="item3">
      <template #icon>
        <t-icon name="play-circle" />
      </template>
      视频区
    </t-menu-item>
    <t-menu-item value="item4" :disabled="true">
      <template #icon>
        <t-icon name="edit-1" />
      </template>
      资源编辑
    </t-menu-item>
    <template #operations>
      <t-icon class="t-menu__operations-icon" :name="iconName" @click="changeCollapsed" />
    </template>
  </t-menu>
</template>

<script setup>
import { ref, computed } from 'vue';

const collapsed = ref(true);

const iconName = computed(() => (collapsed.value ? 'chevron-right' : 'chevron-left'));

const changeCollapsed = () => {
  collapsed.value = !collapsed.value;
};
</script>
