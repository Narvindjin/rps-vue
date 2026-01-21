<script setup lang="ts">
import Rules from '@/steps/Rules.vue'
import { openModal } from 'jenesius-vue-modal'
</script>

<template>
  <button
    class="default-states pointer-events-auto select-none rounded-lg border-1 cursor-pointer p-2 tracking-[0.2em] text-sm uppercase w-30 md:text-xl md:w-40 xl:w-45 xl:text-2xl border-white"
    type="button"
    @click="openModal(Rules)"
  >
    Rules
  </button>
</template>
