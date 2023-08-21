<template>
  <!-- index page for sa.vue sh.vue -->
  <main>
    <NuxtLink to="/sa">sexual assault</NuxtLink>
    <NuxtLink to="/sh">sexual harrasement</NuxtLink>
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
