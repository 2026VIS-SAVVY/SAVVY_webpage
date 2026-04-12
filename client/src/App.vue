<template>
  <div id="app">
    <IntroOverlay v-if="showIntro" @complete="handleIntroComplete" />

    <div class="page-content" :class="{ 'page-content--ready': !showIntro }">
      <HeroSection />
      <TeaserSection />
      <AbstractSection />
      <VideoSection />
      <WorkflowSection />
      <DatasetSection />
      <CodeSection />
      <ReferencesSection />
    </div>
  </div>
</template>

<script setup>
import { onBeforeUnmount, ref, watch } from 'vue'
import HeroSection from './components/HeroSection.vue'
import TeaserSection from './components/TeaserSection.vue'
import AbstractSection from './components/AbstractSection.vue'
import VideoSection from './components/VideoSection.vue'
import WorkflowSection from './components/WorkflowSection.vue'
import DatasetSection from './components/DatasetSection.vue'
import CodeSection from './components/CodeSection.vue'
import ReferencesSection from './components/ReferencesSection.vue'
import IntroOverlay from './components/IntroOverlay.vue'

const showIntro = ref(true)

const updateScrollLock = (locked) => {
  document.documentElement.classList.toggle('intro-lock', locked)
  document.body.classList.toggle('intro-lock', locked)
}

watch(
  showIntro,
  (locked) => {
    updateScrollLock(locked)
  },
  { immediate: true },
)

onBeforeUnmount(() => {
  updateScrollLock(false)
})

const handleIntroComplete = () => {
  showIntro.value = false
}
</script>

<style>
#app {
  min-height: 100vh;
  width: 100%;
  max-width: none !important;
  overflow-x: hidden;
  position: relative;
  background: linear-gradient(150deg, #13131f 0%, #16213e 55%, #0f3460 100%);
}

.page-content {
  opacity: 0;
  transform: scale(1.015);
  filter: blur(18px);
  transition:
    opacity 0.8s ease,
    transform 1s cubic-bezier(0.22, 1, 0.36, 1),
    filter 0.8s ease;
  will-change: opacity, transform, filter;
}

.page-content--ready {
  opacity: 1;
  transform: none;
  filter: none;
}
</style>
