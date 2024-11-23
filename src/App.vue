<template>
  <PrincipalHeader :text="data.name" />

  <main>
    <section>
      <Carousel :content="data.days" />
    </section>
  </main>
</template>

<script setup lang="ts">
import { data } from './data'
import { Carousel, PrincipalHeader } from './components'
</script>

<style scoped>
section {
  display: flex;
  justify-items: center;
  padding-inline: 0.4rem;
}
</style>
