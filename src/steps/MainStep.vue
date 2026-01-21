<script lang="ts">
import Container from '@/components/Container.vue'
import Option, { type Type } from '@/components/Option.vue'
import { defineComponent } from 'vue'
import GameStep from './GameStep.vue'

class Button {
  constructor(position: number, transitionLength: number, type: Type) {
    this.position = position
    this.key = position
    this.transitionLength = transitionLength
    this.type = type
    this.setState()
  }
  setState() {
    if (this.position === 0) {
      if (this.circled) {
        this.circled = false
        this.state = 'final'
        setTimeout(() => {
          this.setState()
        }, this.transitionLength)
      } else {
        window.requestAnimationFrame(() => {
          const transitionLength = this.transitionLength
          this.transitionLength = 0
          window.requestAnimationFrame(() => {
            this.state = 'first'
            window.requestAnimationFrame(() => {
              this.transitionLength = transitionLength
            })
          })
        })
      }
    } else if (this.position === 1) {
      this.state = 'second'
    } else {
      this.state = 'third'
    }
  }
  uptickPosition() {
    this.transitioning = true
    this.position++
    if (this.position > 2) {
      this.position = 0
      this.circled = true
    }
    setTimeout(() => {
      this.transitioning = false
    }, this.transitionLength)
    this.setState()
  }
  position: number
  key: number = 0
  type: Type = 'paper'
  instant: boolean = false
  circled: boolean = false
  transitioning: boolean = false
  transitionLength: number = 0
  state: 'first' | 'second' | 'third' | 'final' = 'first'
}

const animationLength = 700

type SelectedOption = 'rock' | 'paper' | 'scissors'

interface DataInterface {
  buttonArray: Button[]
  intervalId: number
  menuStep: boolean
  beginHide: boolean
  selectedOption: SelectedOption
  stepTransitionTime: number
}

export default defineComponent({
  data(): DataInterface {
    return {
      buttonArray: [
        new Button(0, animationLength, 'paper'),
        new Button(1, animationLength, 'rock'),
        new Button(2, animationLength, 'scissors'),
      ],
      intervalId: 0,
      menuStep: true,
      selectedOption: 'rock',
      stepTransitionTime: 300,
      beginHide: false,
    }
  },
  components: {
    Option,
    Container,
    GameStep,
  },
  methods: {
    uptickCurrent() {
      for (const button of this.buttonArray) {
        button.uptickPosition()
      }
    },
    enableInterval() {
      if (!this.intervalId) {
        this.intervalId = setInterval(this.uptickCurrent, 4000)
      }
    },
    disableInterval() {
      clearInterval(this.intervalId)
      this.intervalId = 0
    },
    enterHandler() {
      if (this.intervalId) {
        this.disableInterval()
      }
    },
    leaveHandler() {
      if (!this.intervalId) {
        this.enableInterval()
      }
    },
    hideHandler() {
      this.beginHide = true
      this.disableInterval()
      setTimeout(() => {
        this.menuStep = false
        this.disableInterval()
      }, this.stepTransitionTime)
    },
    showHandler() {
      window.requestAnimationFrame(() => {
        this.menuStep = true
        this.enableInterval()
        window.requestAnimationFrame(() => {
          this.beginHide = false
        })
      })
    },
  },
  mounted() {
    this.enableInterval()
    window.addEventListener('focus', () => {
      if (!this.intervalId) {
        this.enableInterval()
      }
    })
    window.addEventListener('blur', () => {
      this.disableInterval()
    })
  },
})
</script>

<template>
  <Container>
    <div class="relative">
      <GameStep
        @close="
          () => {
            showHandler()
          }
        "
        :selected-option="selectedOption"
        :enabled="!menuStep"
        :stepTime="stepTransitionTime"
      />
      <section
        class="flex py-30 md:pb-50 xl:pb-55 row justify-center animation-base"
        :class="[menuStep ? '' : 'invisible', beginHide ? 'hideStep' : '']"
        :style="{ transitionDuration: stepTransitionTime + 'ms' }"
      >
        <div class="flex relative aspect-313/278 max-w-[55%] w-55 md:w-75 xl:w-90">
          <svg
            class="absolute w-full h-full"
            viewBox="0 0 313 278"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke="#000"
              stroke-width="15"
              fill="none"
              opacity=".2"
              d="M156.5 262 300 8H13z"
            />
          </svg>
          <div class="relative w-full h-full">
            <div
              class="option absolute w-[75%] xl:w-[65%] aspect-square"
              v-for="button in buttonArray"
              @mouseenter="enterHandler"
              @mouseleave="leaveHandler"
              :key="button.key"
              :style="{ transitionDuration: button.transitionLength + 'ms' }"
              :class="[button.transitioning ? 'transitioning' : '', button.state]"
            >
              <Option
                @click="
                  () => {
                    if (!beginHide) {
                      selectedOption = button.type
                      hideHandler()
                    }
                  }
                "
                class="cursor-pointer transition focus-visible:**:data-svg:scale-115 hover:**:data-svg:scale-115"
                :type="button.type"
              ></Option>
            </div>
          </div>
        </div>
      </section>
    </div>
  </Container>
</template>

<style>
.option {
  offset-path: polygon(0% 0%, 100% 0%, 50% 100%);
  offset-anchor: center;
  cursor: pointer;
  transition-timing-function: ease-in-out;
  offset-rotate: 0deg;
  transition-property: offset-distance;
}

.first {
  offset-distance: 0%;
  transform: rotate(0deg);
}

.second {
  offset-distance: 33%;
}

.third {
  offset-distance: 66%;
}

.transitioning {
  pointer-events: none;
  cursor: default;
}

.final {
  offset-distance: 100%;
}

.hideStep {
  opacity: 0;
}
</style>
