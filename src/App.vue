<script setup>
  import TitleSection from './components/TitleSection.vue'

  import { Twitch, Youtube, User, Music, Server, Users } from 'lucide-vue-next'

  const links = [
    { icon: Twitch, label: 'Ma chaine Twitch', url: 'https://twitch.tv/selunik_' },
    { icon: Youtube, label: 'Ma chaine YouTube', url: 'https://youtube.com/@selunikk' },
    { icon: User, label: 'Mon Portfolio', url: 'https://selunik.wsht.fr' },
    {
      icon: Music,
      label: 'Mon Spotify',
      url: 'https://open.spotify.com/user/1tspgv4pq4ufmsrgpn0rjgb9q?si=af70b6768235489e',
    },
    { icon: Server, label: 'wehosting.fr', url: 'https://www.wehosting.fr' },
    { icon: Users, label: 'Mon serveur Discord', url: 'https://discord.gg/FgtXcsQ8yv' },
  ]
</script>

<template>
  <main class="bg-[var(--color-mirage)] min-h-screen flex flex-col items-center px-2">
    <TitleSection />
    <div class="w-full max-w-xl flex flex-col gap-4 mt-8">
      <a
        v-for="(link, i) in links"
        :key="link.label"
        :href="link.url"
        target="_blank"
        class="flex items-center gap-3 px-6 py-4 rounded-xl bg-[var(--color-vanilla)] text-[var(--color-mirage)] font-semibold text-lg shadow transition hover:bg-[var(--color-mirage)] hover:text-[var(--color-sand)] link-animate btn-bounce"
        :style="{ animationDelay: 0.5 + i * 0.08 + 's' }"
      >
        <component :is="link.icon" class="text-2xl icon-animate" />
        <span>{{ link.label }}</span>
      </a>
    </div>
  </main>
</template>

<style scoped>
:global(html, body) {
  overflow: hidden;
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  background: #312f2c !important;
}

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
.link-animate {
  transition:
    transform 0.32s cubic-bezier(0.22, 1, 0.36, 1),
    box-shadow 0.32s cubic-bezier(0.22, 1, 0.36, 1),
    background 0.32s cubic-bezier(0.22, 1, 0.36, 1),
    color 0.32s cubic-bezier(0.22, 1, 0.36, 1);
  will-change: transform, box-shadow, background, color;
}
.link-animate:hover {
  transform: scale(1.08) translateY(-6px) rotate(-2deg) skewY(-2deg);
  box-shadow: 0 12px 36px 0 #45464788;
  background: linear-gradient(90deg, var(--color-jade) 0%, var(--color-sand) 100%);
  transition: 400ms cubic-bezier(0.22, 1, 0.36, 1);
}
.icon-animate {
  transition:
    color 0.22s,
    transform 0.5s cubic-bezier(0.22, 1, 0.36, 1);
  will-change: transform, color;
}
.link-animate:hover .icon-animate {
  color: var(--color-sand);
  transform: scale(1.32) rotate(-28deg) skewY(-10deg) skewX(4deg);
}
.btn-bounce {
  opacity: 0;
  animation: btnBounceIn 1.1s cubic-bezier(0.22, 1, 0.36, 1) both;
}
@keyframes btnBounceIn {
  0% {
    opacity: 0;
    transform: translateY(100px) scale(0.92) skewY(6deg);
  }
  60% {
    opacity: 1;
    transform: translateY(-22px) scale(1.08) skewY(-2deg);
  }
  80% {
    transform: translateY(8px) scale(0.98) skewY(1deg);
  }
  100% {
    opacity: 1;
    transform: translateY(0) scale(1) skewY(0);
  }
}
</style>
