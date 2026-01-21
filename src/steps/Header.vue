<script setup lang="ts">
import Container from '@/components/Container.vue'
import type { ScoreInterface } from '@/views/HomeView.vue'
import { inject } from 'vue'
const { score, setScore } = inject<ScoreInterface>('score')!
</script>

<template>
  <Container>
    <header class="flex shrink-0 w-full py-10 xl:py-15">
      <div
        class="flex flex-row items-center justify-between w-full pl-5 py-2 pr-2 xl:pl-8 xl:pr-5 xl:py-5 border-3 rounded-lg border-gray"
      >
        <h1
          class="text-2xl select-none leading-[0.8] md:text-3xl xl:text-[42px] uppercase font-bold"
        >
          Rock <br />Paper <br />Scissors
        </h1>
        <button
          type="button"
          @click="setScore(0)"
          class="flex flex-col rounded-md w-25 md:w-35 h-full p-3 xl:w-45 bg-white text-blue-dark items-center"
        >
          <span class="uppercase text-base md:text-lg xl:text-xl tracking-widest font-bold"
            >Score</span
          >
          <span
            class="uppercase font-bold text-5xl md:text-6xl xl:text-7xl text-gray leading-[0.9]"
            >{{ score }}</span
          >
        </button>
      </div>
    </header>
  </Container>
</template>
