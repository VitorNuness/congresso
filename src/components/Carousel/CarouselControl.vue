<template>
  <div class="carousel-control">
    <div class="content">
      <button @click="$emit('previousClick')" :disabled="!props.hasPrevious">
        <span v-if="props.hasPrevious" class="material-symbols-outlined">
          arrow_left
        </span>
      </button>
      <div class="carousel-text">
        <p>DIA</p>
        <h2>{{ props.mainText?.split('-')[0] }}</h2>
      </div>
      <button @click="$emit('nextClick')" :disabled="!props.hasNext">
        <span v-if="props.hasNext" class="material-symbols-outlined">
          arrow_right
        </span>
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  mainText: String,
  hasPrevious: Boolean,
  previousButtonContent: String,
  hasNext: Boolean,
  nextButtonContent: String,
})
</script>

<style lang="css" scoped>
.carousel-control {
  position: fixed;
  z-index: 1000;
  bottom: 1.8rem;
  left: 0;

  width: 100%;
  padding-inline: 0.8rem;
}

.content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-block: 0.28rem;
  background: #e7e7e732;
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  border-radius: 4px;
  border: 1px solid #e72e5c4e;
}

.carousel-text {
  text-align: center;
}

.carousel-text p {
  position: absolute;
  top: 0.2rem;
  left: 0;
  width: 100%;
  font-size: 8pt;
}

h2 {
  font-size: 28pt;
  text-shadow: 0 0 16px #e72e5c91;
}

button {
  align-items: center;
  display: flex;
  justify-content: center;
  width: 100em;
  height: 100%;

  background-color: #ffdbdb00;
  border: none;
  font-weight: 600;
}

button:first-of-type {
  justify-content: start;
}

button:last-of-type {
  justify-content: end;
}
</style>
