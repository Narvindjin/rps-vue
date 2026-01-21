<script setup lang="ts">
import { closeModal } from 'jenesius-vue-modal'
import Modal from '@/components/Modal.vue'
</script>

<template>
  <Modal>
    <div
      class="bg-white flex flex-col items-center min-h-dvh md:min-h-fit md:w-100 relative md:rounded-md md:py-8 md:px-10 justify-between md:items-baseline w-full"
    >
      <h2 class="uppercase text-dark-text text-4xl mt-20 mb-20 md:mb-9 md:mt-0 font-bold">Rules</h2>
      <div class="max-w-sm w-[90%] md:self-center md:w-[100%]">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 304 270">
          <defs>
            <linearGradient id="a" x1="50%" x2="50%" y1="0%" y2="100%">
              <stop offset="0%" stop-color="#fff" stop-opacity=".1" />
              <stop offset="100%" stop-color="#fff" stop-opacity="0" />
            </linearGradient>
            <linearGradient id="b" x1="50%" x2="50%" y1="0%" y2="100%">
              <stop offset="0%" stop-color="#fff" stop-opacity=".1" />
              <stop offset="100%" stop-color="#fff" stop-opacity="0" />
            </linearGradient>
          </defs>
          <g fill="none" fill-rule="evenodd">
            <ellipse cx="53.19" cy="54.81" fill="#b1b4c5" rx="53.19" ry="54.81" />
            <ellipse cx="53.19" cy="52.38" fill="url(#a)" rx="53.19" ry="52.38" />
            <g transform="translate(12.36 12.42)">
              <ellipse cx="40.83" cy="41.04" fill="#e1e4ed" rx="40.83" ry="41.04" />
              <path
                fill="#8a90ac"
                fill-rule="nonzero"
                d="M56.7 30.42a2 2 0 0 0-.9-.15q-.65.05-.96.48c-1.18 1.67-2.14 4.81-2.92 7.34a35 35 0 0 1-1.18 3.47c-.37-2.08.04-9.7.2-12.63v-.04c.11-2.04.13-2.4.1-2.56q-.26-1.67-1.31-2.18c-.71-.33-1.63-.18-2.62.42-.5.3-.64 1.35-1.07 6.07v.02c-.23 2.6-.77 8.57-1.44 9.56-.75-1.4-1.78-9.3-2.23-12.72q-.45-3.58-.61-4.2c-.26-.86-1.35-1.6-2.42-1.64-.9-.05-1.63.41-1.98 1.21-.66.74-.43 3.18.3 8.96.34 2.76 1.06 8.44.6 9.08-.89-.1-2.42-3.66-4.55-10.59-.6-1.94-.78-2.52-.97-2.78-.36-.89-1.6-1.58-2.7-1.5l-.27.04c-.58.11-1.9.65-1.62 3.13a80 80 0 0 0 2.45 8.4l.01.05c.5 1.47.96 2.85 1.4 4.4 1 3.62.61 5.87.6 5.9q-.05.34-.2.42l-.15.03c-.32.03-.8-.19-1.05-.33-.57-1.1-3.4-6.33-5.97-7.05l-.09-.03h-.1q-1.41.15-2.05 1.08c-.67.97-.4 2.22-.32 2.47l.03.09c.02.04 2.08 3.83 2.4 5.59.28 1.5 1.7 3.15 2.84 4.46l.05.06q.56.64.94 1.14c3.32 3.5 8.56 6.43 8.6 6.45q1 .75 1.06 1.37a.6.6 0 0 1-.12.43l-.11.12.72.7L52.93 64l.59-2.73a55 55 0 0 0 1.43-14.32c0-.24.52-2.58.93-4.47l.01-.05c.82-3.76 1.84-8.44 2.04-10.22.08-.76-.4-1.46-1.23-1.78z"
              />
            </g>
            <g transform="translate(196)">
              <ellipse cx="53.69" cy="54.81" fill="#b1b4c5" rx="53.69" ry="54.81" />
              <ellipse cx="53.69" cy="52.38" fill="url(#b)" rx="53.69" ry="52.38" />
              <g transform="translate(12.47 12.42)">
                <ellipse cx="41.21" cy="41.04" fill="#e1e4ed" rx="41.21" ry="41.04" />
                <path
                  fill="#8a90ac"
                  fill-rule="nonzero"
                  d="m30.46 40.7 4.45-6.24a9 9 0 0 0-8.03 2.4c-4.4 4.36-6.17 13.8-6.54 16.09l11.15 11.1c2-.17 10.9-1.35 19.46-9.88.09-.18 2.18-1.72.47-3.42a2.13 2.13 0 0 0-3 .04 1.05 1.05 0 0 1-1.49.01 1.04 1.04 0 0 1 .02-1.49l3.02-3.01c1.54-1.53.1-4.12-2.06-3.5l-2.47 2.12a1.07 1.07 0 0 1-1.5-.1c-.38-.45-.3-1.12.14-1.5 8.65-7.56 7.38-6.65 12.95-11.85 2.08-1.72-.53-4.77-2.58-3.03L40.98 40.51a1.05 1.05 0 0 1-1.38-.02c-.44-.38-.45-.93-.16-1.37l9.4-14.54c1.36-1.86-1.34-3.91-2.78-2.05l-13.9 19.35a1.05 1.05 0 0 1-1.47.26 1 1 0 0 1-.24-1.45"
                />
              </g>
            </g>
            <g transform="translate(98 160)">
              <ellipse cx="53.69" cy="54.81" fill="#b1b4c5" rx="53.69" ry="54.81" />
              <ellipse cx="53.69" cy="52.38" fill="url(#b)" rx="53.69" ry="52.38" />
              <g transform="translate(12.47 12.42)">
                <ellipse cx="41.21" cy="41.04" fill="#e1e4ed" rx="41.21" ry="41.04" />
                <path
                  fill="#8a90ac"
                  fill-rule="nonzero"
                  d="M57.18 35.15c-.48-6-7.2-5.38-7.2-5.38-2.85-5.01-7.29-1.39-7.29-1.39-3.41-4.9-7.69-.36-7.69-.36-7.37-.8-7.08 5.24-7.08 5.24-.18 1.92 1.04 7.85 1.04 7.85-1.1-3.42-3.47-.59-3.47-.59-2.92 4.5-.72 6.97-.72 6.97 3.95 4.63 12.36 10.18 12.36 10.18 3.04 1.75 1.75 3.3 1.75 3.3l18.42-3.04.43-3.5c2.8-8.47-.55-19.28-.55-19.28"
                />
              </g>
            </g>
            <text
              fill="#b1b4c5"
              font-family="BarlowSemiCondensed-Bold, Barlow Semi Condensed"
              font-size="13"
              font-style="condensed"
              font-weight="bold"
            >
              <tspan x="134" y="31">BEATS</tspan>
            </text>
            <text
              fill="#b1b4c5"
              font-family="BarlowSemiCondensed-Bold, Barlow Semi Condensed"
              font-size="13"
              font-style="condensed"
              font-weight="bold"
            >
              <tspan x="40" y="147">BEATS</tspan>
            </text>
            <text
              fill="#b1b4c5"
              font-family="BarlowSemiCondensed-Bold, Barlow Semi Condensed"
              font-size="13"
              font-style="condensed"
              font-weight="bold"
            >
              <tspan x="235" y="147">BEATS</tspan>
            </text>
            <g fill="#b1b4c5" transform="matrix(-1 0 0 1 177 39)">
              <rect width="50" height="4" y="10" rx="2" />
              <path
                d="m41.96 2.02 8.6 8.72c.7.73.7 1.9-.02 2.62a1.83 1.83 0 0 1-2.6-.01l-8.59-8.73A1.86 1.86 0 0 1 39.36 2a1.83 1.83 0 0 1 2.6.02"
              />
              <path
                d="m39.35 19.38 8.59-8.73a1.83 1.83 0 0 1 2.6 0c.72.71.73 1.88.01 2.6L41.96 22a1.83 1.83 0 0 1-2.6 0 1.86 1.86 0 0 1-.01-2.6"
              />
            </g>
            <g fill="#b1b4c5" transform="rotate(235 68.3 42.99)scale(-1 1)">
              <rect width="50" height="4" y="10" rx="2" />
              <path
                d="m41.96 2.02 8.6 8.72c.7.73.7 1.9-.02 2.62a1.83 1.83 0 0 1-2.6-.01l-8.59-8.73A1.86 1.86 0 0 1 39.36 2a1.83 1.83 0 0 1 2.6.02"
              />
              <path
                d="m39.35 19.38 8.59-8.73a1.83 1.83 0 0 1 2.6 0c.72.71.73 1.88.01 2.6L41.96 22a1.83 1.83 0 0 1-2.6 0 1.86 1.86 0 0 1-.01-2.6"
              />
            </g>
            <g fill="#b1b4c5" transform="rotate(-55 240.02 -103.65)">
              <rect width="50" height="4" y="10" rx="2" />
              <path
                d="m41.96 2.02 8.6 8.72c.7.73.7 1.9-.02 2.62a1.83 1.83 0 0 1-2.6-.01l-8.59-8.73A1.86 1.86 0 0 1 39.36 2a1.83 1.83 0 0 1 2.6.02"
              />
              <path
                d="m39.35 19.38 8.59-8.73a1.83 1.83 0 0 1 2.6 0c.72.71.73 1.88.01 2.6L41.96 22a1.83 1.83 0 0 1-2.6 0 1.86 1.86 0 0 1-.01-2.6"
              />
            </g>
          </g>
        </svg>
        <span class="visually-hidden"
          >Scissors beat paper, paper beats rock, rock beats scissors</span
        >
      </div>
      <button
        class="w-7 default-states h-7 mb-15 mt-20 mx-auto md:absolute md:top-9 md:right-8 md:mt-0 md:mb-0"
        type="button"
        @click="closeModal()"
      >
        <span class="visually-hidden">Close</span>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
          <path
            fill="#3b4262"
            fill-rule="evenodd"
            d="m16.97 0 2.12 2.12-7.42 7.43 7.42 7.42-2.12 2.12-7.42-7.42-7.43 7.42L0 16.97l7.43-7.42L0 2.11 2.12 0l7.43 7.43z"
            opacity=".25"
          />
        </svg>
      </button>
    </div>
  </Modal>
</template>
