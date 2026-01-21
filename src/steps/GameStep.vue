<script setup lang="ts">
import Option from '@/components/Option.vue'
import type { ScoreInterface } from '@/views/HomeView.vue'
import { watch, ref, type Ref, inject, reactive, isReactive, h } from 'vue'
const emit = defineEmits(['close'])
class AnimationObject {
  showHouse = false
  showResult = false
  showPlayer = false
  fightStart = false
  animating = false
  hiding = true
  loser: null | 'player' | 'house' = null
  animationTime = 0
  fightTime = 850

  constructor(animationTime: number) {
    this.animationTime = animationTime
  }
}
const props = defineProps<{
  enabled: boolean
  selectedOption: 'paper' | 'rock' | 'scissors'
  stepTime: number
}>()
const animationObject = reactive(new AnimationObject(props.stepTime))
const animateSecondStep = (result: 'win' | 'lose' | 'draw') => {
  setTimeout(() => {
    animationObject.fightStart = true
    setTimeout(() => {
      if (result === 'win') {
        animationObject.loser = 'house'
      } else if (result === 'lose') {
        animationObject.loser = 'player'
      } else {
        animationObject.loser = null
      }
      animationObject.showResult = true
    }, animationObject.fightTime / 2)
    setTimeout(() => {
      animationObject.fightStart = false
      animationObject.animating = false
    }, animationObject.fightTime)
  }, animationObject.animationTime)
}
const handleClose = () => {
  animationObject.hiding = true
  setTimeout(() => {
    requestAnimationFrame(() => {
      emit('close')
      animationObject.loser = null
      animationObject.showPlayer = false
      animationObject.showHouse = false
      animationObject.showResult = false
    })
  }, animationObject.animationTime)
}
const { score, setScore } = inject<ScoreInterface>('score')!
const result: Ref<'win' | 'lose' | 'draw'> = ref('draw')
const houseChoice: Ref<'paper' | 'rock' | 'scissors' | ''> = ref('')
const getRandomChoice = () => {
  const number = Math.floor(Math.random() * 3)
  if (number === 0) {
    return 'paper'
  } else if (number === 1) {
    return 'rock'
  } else {
    return 'scissors'
  }
}

const startAnimation = () => {
  animationObject.animating = true
  animationObject.showHouse = false
  animationObject.showResult = false
  animationObject.loser = null
}

const handleHouseChoice = async () => {
  const value = getRandomChoice()
  startAnimation()
  setTimeout(() => {
    houseChoice.value = value
    animationObject.showHouse = true
    if (props.selectedOption === houseChoice.value) {
      result.value = 'draw'
    } else if (houseChoice.value === 'paper') {
      if (props.selectedOption === 'scissors') {
        result.value = 'win'
      } else {
        result.value = 'lose'
      }
    } else if (houseChoice.value === 'rock') {
      if (props.selectedOption === 'paper') {
        result.value = 'win'
      } else {
        result.value = 'lose'
      }
    } else {
      if (props.selectedOption === 'rock') {
        result.value = 'win'
      } else {
        result.value = 'lose'
      }
    }
    animateSecondStep(result.value)
    setTimeout(() => {
      if (result.value === 'win') {
        setScore(score.value + 1)
      } else if (result.value === 'lose' && score.value > 0) {
        setScore(score.value - 1)
      }
    }, animationObject.fightTime)
  }, animationObject.animationTime)
}
watch(
  () => props.enabled,
  (newValue, oldValue) => {
    if (newValue && newValue !== oldValue) {
      animationObject.hiding = false
      setTimeout(() => {
        animationObject.showPlayer = true
        handleHouseChoice()
      }, animationObject.animationTime)
    }
  },
)
</script>

<template>
  <section
    class="flex flex-col h-full w-[110%] left-[-5%] md:left-0 md:w-full md:pb-20 absolute animate-opacity xl:w-[140%] xl:left-[-20%] xl:pb-0"
    :style="{ transitionDuration: animationObject.animationTime + 'ms' }"
    :class="[enabled ? '' : 'invisible', animationObject.hiding ? 'no-opacity' : '']"
  >
    <div class="flex flex-col mb-auto xl:mb-0 xl:mt-14">
      <div class="flex flex-row w-full xl:order-2 overflow-hidden">
        <div class="flex w-full relative">
          <div
            class="mb-8 w-full relative max-w-50 md:max-w-65 xl:max-w-90 aspect-square xl:mb-0 xl:mt-20"
            :class="[animationObject.fightStart ? 'animate-left' : '']"
            :style="{ animationDuration: animationObject.fightTime + 'ms' }"
          >
            <div
              class="flex absolute bottom-0 left-0 w-full h-full"
              :style="{ animationDuration: animationObject.fightTime + 'ms' }"
              :class="[animationObject.fightStart ? 'animate-lift' : '']"
            >
              <Option
                style="cursor: default"
                :style="{ transitionDuration: animationObject.animationTime + 'ms' }"
                class="animation-base"
                :class="[
                  animationObject.showPlayer ? '' : 'hide',
                  animationObject.loser === 'player' ? 'greyed' : '',
                ]"
                :type="selectedOption"
                tabindex="-1"
              ></Option>
            </div>
          </div>
        </div>
        <div class="flex w-full justify-end">
          <div
            class="mb-8 w-full relative max-w-50 md:max-w-65 xl:max-w-90 aspect-square xl:mb-0 xl:mt-20"
            :class="[animationObject.fightStart ? 'animate-right' : '']"
            :style="{ animationDuration: animationObject.fightTime + 'ms' }"
          >
            <div
              class="flex absolute bottom-0 left-0 w-full h-full"
              :style="{ animationDuration: animationObject.fightTime + 'ms' }"
              :class="[animationObject.fightStart ? 'animate-lift' : '']"
            >
              <Option
                style="cursor: default"
                :style="{ transitionDuration: animationObject.animationTime + 'ms' }"
                class="animation-base"
                :class="[
                  animationObject.showHouse ? '' : 'hide',
                  animationObject.loser === 'house' ? 'greyed' : '',
                ]"
                :type="houseChoice"
                tabindex="-1"
              ></Option>
            </div>
          </div>
        </div>
      </div>
      <div class="flex flex-row justify-between">
        <div class="flex justify-center w-full max-w-50 md:max-w-65 xl:max-w-90">
          <span class="text-lg xl:text-3xl uppercase tracking-widest font-bold animation-base"
            >You picked</span
          >
        </div>
        <div class="flex justify-center w-full max-w-50 md:max-w-65 xl:max-w-90">
          <span
            class="text-lg xl:text-3xl uppercase tracking-widest font-bold text-center animation-base"
            >The house picked</span
          >
        </div>
      </div>
    </div>
    <div
      class="flex flex-col mt-15 items-center self-center xl:absolute xl:top-0 xl:bottom-0 xl:my-auto animation-base"
      :class="[animationObject.showResult ? '' : 'hide']"
      :style="{ transitionDuration: animationObject.animationTime + 'ms' }"
    >
      <h2 class="text-white text-7xl mb-5 font-bold uppercase">
        <span v-if="result === 'win'">You win</span>
        <span v-if="result === 'draw'">Draw</span>
        <span v-if="result === 'lose'">You lose</span>
      </h2>
      <button
        type="button"
        @click="handleHouseChoice"
        class="transition w-70 active:text-red-dark hover:text-red-dark focus-visible:text-red-dark active:opacity-80 tracking-widest rounded-lg text-xl xl:text-xl uppercase p-4 mb-5 bg-white font-bold text-gray"
        :class="[animationObject.animating ? 'pointer-events-none' : '']"
      >
        Play again
      </button>
      <button
        type="button"
        @click="handleClose()"
        class="text-xl transition hover:text-gold-dark focus-visible:text-gold-dark active:opacity-80 active:text-gold-dark"
        :class="[animationObject.animating ? 'pointer-events-none' : '']"
      >
        Change your pick
      </button>
    </div>
  </section>
</template>

<style scoped>
.animate-left {
  animation: leftPath ease-out;
}

.animate-right {
  animation: rightPath ease-out;
}

.animate-lift {
  animation: pseudoLift linear;
}
.greyed {
  filter: grayscale(100%);
}

.animate-opacity {
  transition-property: opacity;
  transition-timing-function: ease-in-out;
}

.no-opacity {
  opacity: 0;
}

@keyframes leftPath {
  0% {
    left: 0;
  }
  35% {
    left: 100%;
    transform: translateX(-100%) rotate(65deg);
  }
  70% {
    transform: translateX(-40%) rotate(-35deg);
  }
  100% {
    left: 0;
    transform: translateX(0) rotate(0);
  }
}

@keyframes rightPath {
  0% {
    right: 0;
  }
  35% {
    right: 100%;
    transform: translateX(100%) rotate(-65deg);
  }
  70% {
    transform: translateX(40%) rotate(35deg);
  }
  100% {
    right: 0;
    transform: translateX(0) rotate(0);
  }
}

@keyframes pseudoLift {
  0% {
    bottom: 0;
  }
  40% {
    bottom: 0;
  }
  65% {
    bottom: 30%;
  }
  90% {
    bottom: 0;
  }
}
</style>
