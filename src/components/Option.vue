<script lang="ts">
import { defineComponent } from 'vue'

export type Type = 'rock' | 'paper' | 'scissors'

export default defineComponent({
  props: {
    type: String,
  },
})
</script>

<template>
  <button
    type="button"
    class="relative flex rounded-full w-full h-full shadow-[0_6px_1px_-1px] md:shadow-[0_7px_1px_-1px] xl:shadow-[0_10px_1px_-1px]"
    :class="[
      type === 'paper' ? 'bg-blue shadow-blue-dark' : '',
      type === 'rock' ? 'bg-red shadow-red-dark' : '',
      type === 'scissors' ? 'bg-gold shadow-gold-dark' : '',
    ]"
  >
    <span class="visually-hidden">
      {{ type }}
    </span>
    <span
      class="absolute flex top-0 bottom-0 left-0 right-0 m-auto w-[77%] aspect-square inset-shadow-[0_6px_1px_-1px] md:inset-shadow-[0_7px_1px_-1px] xl:inset-shadow-[0_10px_1px_-1px] inset-shadow-gray/30 rounded-full bg-gray-200"
    >
      <svg
        v-if:="type === 'paper'"
        xmlns="http://www.w3.org/2000/svg"
        class="aspect-49/59 transition absolute flex top-0 bottom-0 left-0 right-0 m-auto w-[45%]"
        viewBox="0 0 49 59"
        data-svg
      >
        <path
          fill="#3b4262"
          d="M47.13 11.83a3 3 0 0 0-1.24-.2 1.7 1.7 0 0 0-1.3.65c-1.6 2.25-2.92 6.5-3.98 9.9a47 47 0 0 1-1.61 4.7c-.5-2.8.06-13.1.28-17.05v-.06c.15-2.76.17-3.24.14-3.45q-.36-2.27-1.8-2.94c-.96-.45-2.22-.25-3.57.56-.68.4-.86 1.82-1.45 8.19v.03c-.32 3.5-1.06 11.56-1.96 12.9C29.6 23.2 28.2 12.52 27.6 7.9c-.43-3.23-.68-5.1-.84-5.65C26.4 1.06 24.93.06 23.46 0a2.7 2.7 0 0 0-2.7 1.64c-.89 1-.57 4.3.41 12.1.47 3.72 1.44 11.4.83 12.26-1.21-.13-3.3-4.94-6.21-14.3-.82-2.62-1.07-3.4-1.32-3.75-.5-1.2-2.17-2.13-3.67-2.02l-.38.04c-.79.16-2.59.89-2.2 4.23 1.06 4.64 2.21 8.04 3.33 11.35l.02.06c.67 1.98 1.3 3.85 1.9 5.93 1.38 4.9.84 7.94.83 7.97q-.06.47-.29.57l-.19.05a3 3 0 0 1-1.44-.45c-.77-1.48-4.63-8.55-8.13-9.53l-.13-.03H4q-1.94.2-2.8 1.45c-.92 1.32-.54 3-.45 3.34l.05.12c.03.05 2.83 5.16 3.27 7.54.37 2.04 2.31 4.25 3.87 6.03l.06.07q.77.87 1.3 1.55c4.51 4.71 11.66 8.68 11.72 8.71q1.34 1.01 1.44 1.84a.8.8 0 0 1-.16.58l-.16.16.99.96 18.85-1.32.8-3.69a73 73 0 0 0 1.96-19.33c.01-.32.71-3.48 1.27-6.03l.02-.06c1.11-5.08 2.5-11.4 2.77-13.8.12-1.03-.54-1.98-1.68-2.4"
        />
      </svg>
      <svg
        v-if:="type === 'rock'"
        xmlns="http://www.w3.org/2000/svg"
        class="aspect-48/48 transition absolute flex top-0 bottom-0 left-0 right-0 m-auto w-[45%]"
        viewBox="0 0 48 48"
        data-svg
      >
        <path
          fill="#3b4262"
          d="M45.06 12.22c-.64-8.1-9.73-7.27-9.73-7.27-3.84-6.76-9.84-1.86-9.84-1.86-4.6-6.63-10.38-.49-10.38-.49-9.95-1.07-9.57 7.07-9.57 7.07-.23 2.58 1.4 10.59 1.4 10.59-1.47-4.62-4.67-.79-4.67-.79-3.94 6.08-.98 9.41-.98 9.41 5.33 6.25 16.69 13.74 16.69 13.74 4.11 2.36 2.37 4.46 2.37 4.46l24.88-4.11.57-4.72c3.78-11.43-.74-26.03-.74-26.03"
        />
      </svg>
      <svg
        v-if:="type === 'scissors'"
        xmlns="http://www.w3.org/2000/svg"
        class="aspect-51/58 transition absolute flex top-0 bottom-0 left-0 right-0 m-auto w-[45%]"
        viewBox="0 0 51 58"
        data-svg
      >
        <path
          fill="#3b4262"
          d="m13.97 25.7 6.01-8.41c-2.5-.42-7.08-.51-10.84 3.23C3.2 26.42.8 39.16.3 42.25l15.06 14.99c2.71-.23 14.71-1.83 26.28-13.34.12-.25 2.94-2.32.64-4.61a2.9 2.9 0 0 0-4.05.04c-.57.57-1.46.58-2.02.02a1.4 1.4 0 0 1 .02-2.01l4.09-4.07c2.08-2.07.12-5.56-2.78-4.72L34.2 31.4c-.6.53-1.52.44-2.02-.14-.52-.6-.4-1.5.19-2.01 11.68-10.2 9.98-8.98 17.5-16 2.8-2.32-.73-6.44-3.5-4.08L28.18 25.45c-.53.45-1.34.46-1.86-.02-.6-.52-.61-1.26-.22-1.85L38.79 3.94c1.85-2.5-1.8-5.27-3.75-2.75L16.28 27.3c-.45.65-1.36.8-1.98.34a1.4 1.4 0 0 1-.33-1.95z"
        />
      </svg>
    </span>
  </button>
</template>
