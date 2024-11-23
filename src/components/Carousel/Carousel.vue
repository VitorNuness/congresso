<template>
  <div class="carousel">
    <CarouselControl
      :main-text="content[currentIndex]?.date"
      :has-previous="currentIndex > 0"
      :previous-button-content="content[currentIndex - 1]?.date"
      :has-next="currentIndex < content.length - 1"
      :next-button-content="content[currentIndex + 1]?.date"
      @previous-click="currentIndex--"
      @next-click="currentIndex++"
    />
    <article class="carousel-item">
      <div
        v-for="(schedule, index) in content[currentIndex]?.schedules"
        :key="index"
      >
        <details>
          <summary>
            <h3>
              <span>
                {{ schedule.start }} - {{ schedule.end }} | Sala
                {{ schedule.room_number }} - {{ schedule.room_floor }}º andar
              </span>
              <span>{{ schedule.room_name }}</span>
            </h3>
            <span class="material-symbols-outlined">
              arrow_drop_down_circle
            </span>
          </summary>
          <ul>
            <li v-for="lecture in schedule.lectures" :key="lecture.title">
              <h4>{{ lecture.title }}</h4>
              <ul
                v-for="(participant, index) in lecture.participants"
                :key="index"
              >
                <li>
                  {{ participant.name }} / {{ participant.country }} ({{
                    participant.role
                  }})
                </li>
              </ul>
              <hr />
            </li>
          </ul>
        </details>
      </div>
    </article>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import CarouselControl from './CarouselControl.vue'

const props = defineProps(['content'])

const currentIndex = ref(0)
</script>

<style lang="css" scoped>
.carousel-item {
  padding-top: 6vh;
}

.carousel-item div:last-child {
  height: 100vh;
}

summary {
  display: flex;
  align-items: center;
  position: sticky;
  top: 0;
  background: rgb(242, 221, 227);
  background: linear-gradient(
    180deg,
    rgba(242, 221, 227, 1) 0%,
    rgba(242, 221, 227, 0.9570028695071778) 40%,
    rgba(242, 221, 227, 0.5984594521402311) 80%,
    rgba(0, 212, 255, 0) 100%
  );
}

.material-symbols-outlined {
  font-size: 28pt;
}

.carousel-item div h3 {
  position: sticky;
  top: 4px;
  border-radius: 0.24rem;
  display: flex;
  flex-direction: column;
  width: 100%;
  font-size: 12pt;
  font-weight: 400;
  text-align: start;
  padding-block: 0.5rem;
  margin-block: 0.8rem;
}

.carousel-item div h3 span:last-child {
  font-size: 14pt;
  font-weight: bold;
}

.carousel-item div h3 span {
  color: #e72e5c;
}

h4 {
  font-weight: 500;
  font-size: 12pt;
  margin-bottom: 0.8em;
}

li {
  font-size: 8pt;
}

hr {
  border: #a34f62 solid 0.1rem;
  border-radius: 0.2rem;
  margin-block: 2rem;
}
</style>
