<template>
  <div class="app-main">
    <router-view v-slot="{ Component }">
      <transition name="fade-slide">
        <keep-alive :include="cachedViews && cachedViews.map((x: any) => x.name)">
          <component :is="Component" />
        </keep-alive>
      </transition>
    </router-view>
  </div>
</template>

<script lang="ts" setup>
import { useLayoutStore } from '@/layout/store';
import { storeToRefs } from 'pinia';
const store = useLayoutStore();

const { cachedViews } = storeToRefs(store);
</script>

<style lang="scss" scoped>
.app-main {
  padding: 10px;
  // height: calc(100vh - 90px);
  width: 100%;
  flex: 1;
  overflow: hidden;

  // background-color: rgb(223, 223, 223);
  box-sizing: border-box;
  overflow: hidden;
  background: url('../../../assets/img/bg-1.png') repeat;
}

.fade-transition {

  &-enter-active,
  &-leave-active {
    transition: opacity 0.2s ease-in-out;
  }

  &-enter-from,
  &-leave-to {
    opacity: 0;
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* fade-slide */
.fade-slide-leave-active,
.fade-slide-enter-active {
  transition: all 0.3s;
}

.fade-slide-enter-from {
  opacity: 0;
  transform: translateX(-30px);
}

.fade-slide-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

// ///////////////////////////////////////////////
// Fade Bottom
// ///////////////////////////////////////////////

// Speed: 1x
.fade-bottom-enter-active,
.fade-bottom-leave-active {
  transition: opacity 0.25s, transform 0.3s;
}

.fade-bottom-enter-from {
  opacity: 0;
  transform: translateY(-10%);
}

.fade-bottom-leave-to {
  opacity: 0;
  transform: translateY(10%);
}

// fade-scale
.fade-scale-leave-active,
.fade-scale-enter-active {
  transition: all 0.28s;
}

.fade-scale-enter-from {
  opacity: 0;
  transform: scale(1.2);
}

.fade-scale-leave-to {
  opacity: 0;
  transform: scale(0.8);
}

// ///////////////////////////////////////////////
// Fade Top
// ///////////////////////////////////////////////

// Speed: 1x
.fade-top-enter-active,
.fade-top-leave-active {
  transition: opacity 0.2s, transform 0.25s;
}

.fade-top-enter-from {
  opacity: 0;
  transform: translateY(8%);
}

.fade-top-leave-to {
  opacity: 0;
  transform: translateY(-8%);
}
</style>
