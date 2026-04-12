<template>
  <transition name="intro-fade">
    <div
      v-if="visible"
      class="intro-overlay"
      :class="{ 'intro-overlay--leaving': isLeaving }"
      aria-hidden="true"
    >
      <div class="intro-overlay__bg"></div>
      <div class="intro-overlay__vignette"></div>
      <div class="intro-overlay__grid"></div>

      <div class="intro-overlay__stage">
        <div class="intro-overlay__halo"></div>
        <div class="intro-overlay__wordmark-shell">
          <img
            src="/images/savvy-wordmark.svg"
            alt="SAVVY"
            class="intro-overlay__wordmark"
          />
          <span class="intro-overlay__sheen"></span>
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
import { onBeforeUnmount, onMounted, ref } from 'vue'

const emit = defineEmits(['complete'])

const visible = ref(true)
const isLeaving = ref(false)

let leaveTimer = 0
let completeTimer = 0

onMounted(() => {
  leaveTimer = window.setTimeout(() => {
    isLeaving.value = true
  }, 2200)

  completeTimer = window.setTimeout(() => {
    visible.value = false
    emit('complete')
  }, 3000)
})

onBeforeUnmount(() => {
  window.clearTimeout(leaveTimer)
  window.clearTimeout(completeTimer)
})
</script>

<style scoped>
.intro-overlay {
  position: fixed;
  inset: 0;
  z-index: 100;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  background:
    radial-gradient(circle at 50% 42%, rgba(116, 188, 255, 0.16) 0%, rgba(116, 188, 255, 0.02) 30%, rgba(19, 19, 31, 0) 58%),
    linear-gradient(160deg, #0b101b 0%, #11182a 35%, #13131f 72%, #0c1425 100%);
  isolation: isolate;
}

.intro-overlay__bg,
.intro-overlay__vignette,
.intro-overlay__grid {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.intro-overlay__bg {
  background:
    radial-gradient(circle at 50% 44%, rgba(147, 197, 253, 0.16) 0%, rgba(147, 197, 253, 0.05) 22%, rgba(147, 197, 253, 0) 58%),
    radial-gradient(circle at 50% 50%, rgba(255, 255, 255, 0.05) 0%, rgba(255, 255, 255, 0) 60%);
  animation: introPulse 2.6s ease-in-out forwards;
}

.intro-overlay__vignette {
  background: radial-gradient(circle at center, rgba(0, 0, 0, 0) 42%, rgba(4, 8, 18, 0.72) 100%);
}

.intro-overlay__grid {
  background-image:
    linear-gradient(rgba(163, 189, 255, 0.06) 1px, transparent 1px),
    linear-gradient(90deg, rgba(163, 189, 255, 0.06) 1px, transparent 1px);
  background-size: 48px 48px;
  mask-image: radial-gradient(circle at center, rgba(0, 0, 0, 0.82) 0%, rgba(0, 0, 0, 0.25) 52%, transparent 80%);
  opacity: 0;
  animation: introGrid 2.6s ease forwards;
}

.intro-overlay__stage {
  position: relative;
  width: min(78vw, 980px);
  min-height: 220px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.intro-overlay__halo {
  position: absolute;
  inset: 50% auto auto 50%;
  width: min(68vw, 760px);
  aspect-ratio: 1.9 / 1;
  transform: translate(-50%, -50%);
  background: radial-gradient(circle at center, rgba(107, 160, 255, 0.42) 0%, rgba(78, 130, 244, 0.14) 34%, rgba(31, 67, 135, 0) 74%);
  filter: blur(18px);
  opacity: 0;
  animation: introHalo 2.2s ease forwards;
}

.intro-overlay__wordmark-shell {
  position: relative;
  width: min(74vw, 920px);
  padding: clamp(20px, 3vw, 36px) clamp(18px, 2vw, 28px);
  overflow: hidden;
}

.intro-overlay__wordmark {
  width: 100%;
  display: block;
  transform: translateY(18px) scale(0.94);
  opacity: 0;
  filter: blur(14px) drop-shadow(0 0 0 rgba(0, 0, 0, 0));
  animation: introWordmark 2.35s cubic-bezier(0.2, 0.72, 0.16, 1) forwards;
}

.intro-overlay__sheen {
  position: absolute;
  inset: 0;
  background: linear-gradient(110deg, transparent 15%, rgba(255, 255, 255, 0.06) 42%, rgba(255, 255, 255, 0.58) 50%, rgba(255, 255, 255, 0.06) 58%, transparent 85%);
  transform: translateX(-125%) skewX(-18deg);
  mix-blend-mode: screen;
  opacity: 0;
  animation: introSheen 1.35s ease 0.72s forwards;
}

.intro-overlay--leaving {
  animation: introOverlayExit 0.8s cubic-bezier(0.55, 0, 0.45, 1) forwards;
}

.intro-fade-leave-active {
  transition: opacity 0.35s ease;
}

.intro-fade-leave-to {
  opacity: 0;
}

@keyframes introWordmark {
  0% {
    opacity: 0;
    transform: translateY(18px) scale(0.94);
    filter: blur(14px) drop-shadow(0 0 0 rgba(0, 0, 0, 0));
  }
  32% {
    opacity: 1;
  }
  58% {
    transform: translateY(0) scale(1.01);
    filter: blur(0) drop-shadow(0 0 18px rgba(123, 171, 255, 0.24));
  }
  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
    filter: blur(0) drop-shadow(0 0 24px rgba(123, 171, 255, 0.18));
  }
}

@keyframes introHalo {
  0% {
    opacity: 0;
    transform: translate(-50%, -50%) scale(0.72);
  }
  45% {
    opacity: 1;
  }
  100% {
    opacity: 0.88;
    transform: translate(-50%, -50%) scale(1);
  }
}

@keyframes introPulse {
  0% {
    opacity: 0.42;
    transform: scale(1.08);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}

@keyframes introGrid {
  0% {
    opacity: 0;
    transform: scale(1.06);
  }
  40% {
    opacity: 0.3;
  }
  100% {
    opacity: 0.18;
    transform: scale(1);
  }
}

@keyframes introSheen {
  0% {
    opacity: 0;
    transform: translateX(-125%) skewX(-18deg);
  }
  20% {
    opacity: 0.95;
  }
  100% {
    opacity: 0;
    transform: translateX(130%) skewX(-18deg);
  }
}

@keyframes introOverlayExit {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    transform: scale(1.02);
    filter: blur(10px);
  }
}

@media (max-width: 768px) {
  .intro-overlay__stage {
    width: min(88vw, 720px);
    min-height: 180px;
  }

  .intro-overlay__wordmark-shell {
    width: min(86vw, 720px);
    padding: 18px;
  }

  .intro-overlay__grid {
    background-size: 36px 36px;
  }
}

@media (prefers-reduced-motion: reduce) {
  .intro-overlay,
  .intro-overlay *,
  .intro-fade-leave-active {
    animation-duration: 0.01ms !important;
    animation-delay: 0ms !important;
    transition-duration: 0.01ms !important;
  }
}
</style>
