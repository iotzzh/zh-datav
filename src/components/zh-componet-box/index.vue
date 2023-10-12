<template>
  <div class="component-box">
    <div v-bind="$attrs">
      <slot />
    </div>
    <div class="name">
      {{ name }}
    </div>
  </div>
</template>

<script lang="ts" setup>
  import { toRefs } from 'vue';
  const props = defineProps({
    name: {
      type: String,
      required: true,
    },
  });

  const { name } = toRefs(props);
</script>

<style lang="scss" scoped>
  .component-box {
    height: 100%;
    width: 100%;
    padding: 10px;
  }

  .name {
    position: absolute;
    z-index: 999;
    width: 100%;
    text-align: center;
  }
</style>
