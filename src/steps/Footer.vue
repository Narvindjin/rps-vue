<script setup lang="ts">
import FooterButton from '@/components/FooterButton.vue'
import Container from '@/components/Container.vue'
</script>

<template>
  <Container class="md:absolute md:bottom-[0] md:left-[0] md:right-[0] pointer-events-none xl:mr-0">
    <footer class="flex shrink-0 pt-15 pb-10 row justify-center md:justify-end">
      <FooterButton></FooterButton>
    </footer>
  </Container>
</template>
