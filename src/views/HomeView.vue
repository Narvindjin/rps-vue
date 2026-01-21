<script setup lang="ts">
import { provide, ref, type Ref } from 'vue'
import Footer from '@/steps/Footer.vue'
import Header from '@/steps/Header.vue'
import MainStep from '@/steps/MainStep.vue'
import { container as ModalContainer, config } from 'jenesius-vue-modal'
export interface ScoreInterface {
  score: Ref<number, number>
  setScore: (value: number) => void
}
config({
  animation: 'fade',
})
const scoreFromStorage = localStorage.getItem('rps-score')
let initialScore
if (scoreFromStorage) {
  initialScore = Number(scoreFromStorage)
} else {
  localStorage.setItem('rps-score', '0')
  initialScore = 0
}
const score = ref(initialScore)
const setScore = (value: number) => {
  score.value = value
  localStorage.setItem('rps-score', value + '')
}
const scoreObject: ScoreInterface = {
  score,
  setScore,
}
provide('score', scoreObject)
</script>

<template>
  <div
    class="font-barlow relative font-semibold flex flex-col bg-linear-to-b min-h-full text-white from-bg-gradient-1 to-bg-gradient-2"
  >
    <div class="flex grow flex-col">
      <Header></Header>
      <main class="flex grow flex-col justify-center">
        <MainStep></MainStep>
      </main>
    </div>
    <Footer></Footer>
    <ModalContainer></ModalContainer>
  </div>
</template>
