<script setup>
import { ref, onMounted} from "vue";

import gsap from 'gsap';

const graphics = ref([
  {
    id: 0,
    day: "mon",
    height: 35,
    amount: "$52.36",
  },
  {
    id: 1,
    day: "tue",
    height: 55,
    amount: "$52.36",
  },
  {
    id: 2,
    day: "wed",
    height: 100,
    amount: "$52.36",
  },
  {
    id: 3,
    day: "thu",
    height: 55,
    amount: "$52.36",
  },
  {
    id: 4,
    day: "fri",
    height: 30,
    amount: "$52.36",
  },
  {
    id: 5,
    day: "sat",
    height: 10,
    amount: "$52.36",
  },
  {
    id: 6,
    day: "sun",
    height: 100,
    amount: "$52.36",
  },
]);
const isActive = ref(false);
const activeIndex = ref(null);

onMounted(() => {
  gsap.from(".graphic-inner", {
    height: 0,
    delay: 1,
    duration: 1,
    opacity: 0,
    stagger: 0.25,
  });
});
</script>

<template>
  <div class="stats">
    <div class="graphic" v-for="graphic in graphics" :key="graphic.id">
      <span
        @mouseover="activeIndex = graphic.id"
        @mouseleave="activeIndex = null"
        class="graphic-inner graphic-color"
        :class="
          graphic.height > 75
            ? 'high'
            : graphic.height > 50
            ? 'mid'
            : graphic.height > 25
            ? 'low'
            : 'lower'
        "
      >
        <Transition>
          <span v-if="activeIndex == graphic.id" class="graphic-amount">
            {{ graphic.amount }}
          </span>
        </Transition>
      </span>
      <span class="graphic-text">{{ graphic.day }}</span>
    </div>
  </div>
</template>

<style scoped lang="scss">
.stats {
  display: flex;
  justify-content: space-between;
  padding-bottom: 20px;
  border-bottom: 2px solid hsl(27, 66%, 92%);
  .graphic {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    flex-direction: column;
    .graphic-amount {
      position: absolute;
      top: -25px;
      left: 50%;
      transform: translateX(-50%);
      background-color: hsl(25, 47%, 15%);
      color: #fff;
      font-size: 12px;
      outline: none;
      border: none;
      border-radius: 4px;
      padding: 0.25rem;
      margin-bottom: 5px;
      transition: all 0.3s ease-in;
    }
    .graphic-inner {
      position: relative;
      border-radius: 4px;
      width: 35px;
      transition: all 0.2s ease-in;
      cursor: pointer;
      &:hover {
        background: hsl(186, 34%, 60%);
      }
    }
    .graphic-text {
      font-size: 12px;
      color: hsl(28, 10%, 53%);
    }
    .high {
      height: 100px;
    }
    .mid {
      height: 60px;
    }
    .low {
      height: 35px;
    }
    .lower {
      height: 15px;
    }
  }
}
/* we will explain what these classes do next! */
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
