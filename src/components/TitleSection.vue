<template>
  <div class="flex flex-col items-center pt-12">
    <div
      class="rounded-full mb-4 bg-linear-to-bl from-[var(--color-cyprus)] via-[var(--color-cactus)] to-[var(--color-mirage)] p-1"
    >
      <img
        src="/profile.png"
        alt="Photo de profil"
        class="w-28 h-28 rounded-full shadow-lg profile-spin"
      />
    </div>
    <h1
      class="text-3xl font-bold text-[var(--color-cyprus)] typing-animation mx-auto text-center overflow-hidden pr-2"
    >
      <span class="inline-block typing-text">
        <span
          v-for="(char, i) in displayedText.split('')"
          :key="i"
          :style="{ animationDelay: 0.13 * i + 's' }"
          class="typing-char"
          >{{ char }}</span
        >
      </span>
    </h1>
    <p class="text-center text-[var(--color-sand)] font-semibold mt-2 max-w-xl">
      Salut ! 👋 Je suis Selunik, administrateur systèmes et développeur. Je propose beaucoup de
      services gratuits et surtout open source ! Rejoins moi :)
    </p>
    <div class="flex gap-4 mt-4">
      <a
        href="https://github.com/qrlmza"
        class="text-[var(--color-cyprus)] hover:text-[var(--color-sand)] text-2xl icon-link"
      >
        <Github />
      </a>
      <a
        href="https://selunik.whst.fr"
        class="text-[var(--color-cyprus)] hover:text-[var(--color-sand)] text-2xl icon-link"
      >
        <Globe />
      </a>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, nextTick } from 'vue'
import { Github, Globe } from 'lucide-vue-next'

const correctText = 'selunik'
const displayedText = ref('')

onMounted(async () => {
  displayedText.value = ''
  await nextTick()
  let i = 0
  function typeCorrect() {
    if (i < correctText.length) {
      displayedText.value += correctText[i]
      i++
      setTimeout(typeCorrect, 130)
    }
  }
  typeCorrect()
})
</script>

<style scoped>
.fade-in {
  animation: fadeIn 1.2s cubic-bezier(0.4, 0, 0.2, 1);
}
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
.img-animate {
  animation: popIn 1s cubic-bezier(0.4, 0, 0.2, 1);
}
@keyframes popIn {
  0% {
    opacity: 0;
    transform: scale(0.7) rotate(-8deg);
  }
  80% {
    opacity: 1;
    transform: scale(1.1) rotate(2deg);
  }
  100% {
    opacity: 1;
    transform: scale(1) rotate(0);
  }
}
.profile-spin {
  animation: profileSpin 1.2s cubic-bezier(0.4, 0, 0.2, 1);
}
@keyframes profileSpin {
  0% {
    opacity: 0;
    transform: scale(0.7) rotate(-360deg);
  }
  60% {
    opacity: 1;
    transform: scale(1.08) rotate(20deg);
  }
  100% {
    opacity: 1;
    transform: scale(1) rotate(0);
  }
}
.icon-link {
  transition:
    transform 0.2s,
    color 0.2s;
}
.icon-link:hover {
  transform: scale(1.2) rotate(-8deg);
  color: var(--color-cyprus);
}
.typing-animation {
  width: 0;
  max-width: 8.5ch;
  display: inline-block;
  animation: typing 1.8s cubic-bezier(0.4, 0, 0.2, 1) forwards;
}
.typing-text {
  display: inline-block;
  width: 8.5ch;
  overflow: hidden;
  white-space: nowrap;
}
.typing-char {
  opacity: 0;
  display: inline-block;
  transform: translateY(16px) scale(0.92);
  animation: charAppear 0.55s cubic-bezier(0.4, 0, 0.2, 1) forwards;
}
@keyframes charAppear {
  0% {
    opacity: 0;
    transform: translateY(16px) scale(0.92);
    filter: blur(2px);
  }
  60% {
    opacity: 1;
    transform: translateY(-2px) scale(1.08);
    filter: blur(0.5px);
  }
  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
    filter: blur(0);
  }
}
.typing-cursor {
  display: none;
}
@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 8.5ch;
  }
}
@keyframes blink {
  0%,
  100% {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
}
@keyframes hide-cursor {
  to {
    opacity: 0;
  }
}
</style>
