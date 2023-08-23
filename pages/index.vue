<template>
  <!-- index page for sa.vue sh.vue -->
  <main>
    <NuxtLink to="/accomm-vs-avg">SA rate in accom vs. avg</NuxtLink>
    <NuxtLink to="/sa">SA gender</NuxtLink>
    <NuxtLink to="/sh">SH gender</NuxtLink>
    <NuxtLink to="/location">SA location</NuxtLink>
    <NuxtLink to="/donut">knowledge</NuxtLink>
    <NuxtLink to="/accomm-vs-avg">SA rate in accom vs. avg</NuxtLink>
  </main>
</template>

<style scoped>
main {
  display: flex;
  gap: 2rem;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  font-size: 2rem;
  background-color: #f5f5f5;
}
</style>
