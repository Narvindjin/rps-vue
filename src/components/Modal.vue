<script setup lang="ts"></script>

<template>
  <div class="h-full w-full flex flex-col items-center justify-center pointer-events-none">
    <div class="max-h-fit w-full md:w-auto h-full remove-scrollbar flex overflow-auto">
      <div class="flex flex-col w-full justify-center items-center pointer-events-auto">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<style>
.modal-container {
  z-index: 111;
  background-color: rgba(0, 0, 0, 0.3) !important;
}

.fade-enter-active,
.fade-leave-active,
.fade-enter-active .modal-item,
.fade-leave-active .modal-item {
  transition-duration: 0.3s;
  transition-property: transform, opacity;
  transition-timing-function: ease-in-out;
}

.fade-enter-from .modal-item,
.fade-leave-to .modal-item {
  transform: translateY(-100px);
  opacity: 0;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
