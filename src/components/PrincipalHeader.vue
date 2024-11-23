<template>
  <header>
    <a
      href="https://lp.sbfa.org.br/cbfa2024/"
      target="_blank"
      rel="noopener noreferrer"
      style="font-size: 8pt"
      >{{ props.text }}</a
    >
    <h1>Programação pessoal</h1>
    <p>para</p>
    <a
      href="https://www.instagram.com/luizacalderon.fono/"
      target="_blank"
      rel="noopener noreferrer"
      class="sassy-frass-regular"
      >Luiza M.S. Calderon</a
    >
  </header>
</template>

<script setup lang="ts">
const props = defineProps({
  text: String,
})
</script>

<style lang="css" scoped>
header {
  text-align: center;
  padding-block: 6rem;
}

a {
  text-decoration: none;
  color: #e72e5c;
  padding-block: 4rem;
}

h1 {
  font-weight: 400;
  font-size: 20pt;
}

p {
  font-size: 8pt;
  margin-top: 4rem;
}

.sassy-frass-regular {
  font-size: 28pt;
}
</style>
