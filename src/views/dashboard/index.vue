<template>
  <div class="box">
    <el-row class="row" :gutter="20">
      <el-col :span="12" class="column">
        <ZHComponentBox name="背景动画" style="width: 100%; height: 100%; position: relative"
          ><BgAnimation />
        </ZHComponentBox>
      </el-col>

      <el-col :span="12" class="column">
        <ZHComponentBox name="3d柱状图" style="width: 100%; height: 100%; position: relative"
          ><Bar3d />
        </ZHComponentBox>
      </el-col>
    </el-row>
  </div>
</template>

<script lang="ts" setup>
  import { onMounted, ref, onUnmounted } from 'vue';
  import ZHComponentBox from '@/components/zh-componet-box/index.vue';

  import BgAnimation from '@/components/datav-components/bgAnimation/index.vue';
  import Bar3d from '@/components/datav-components/bar3d/index.vue';
</script>

<style lang="scss" scoped>
  .row,
  .column {
    height: 300px;
  }
</style>
