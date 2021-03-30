<template>
  <header class="nav-bar">
    <!-- TODO: In principle, this entire section should be in a nav region -->
    <ToggleSideBarButton @toggle="$emit('toggle')" :open="open" />

    <NavBarTitle />

    <div class="flex-grow" />

    <nav class="nav">
      <NavLinks />
    </nav>

    <slot name="search" />
  </header>
</template>

<script setup lang="ts">
import { defineEmit, defineProps } from 'vue'
import NavBarTitle from './NavBarTitle.vue'
import NavLinks from './NavLinks.vue'
import ToggleSideBarButton from './ToggleSideBarButton.vue'

defineEmit(['toggle'])
defineProps({
  open: { type: Boolean, required: true }
})
</script>

<style scoped>
.nav-bar {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  z-index: var(--z-index-navbar);
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid var(--c-divider);
  padding: 0.7rem 1.5rem 0.7rem 4rem;
  height: var(--header-height);
  background-color: var(--c-bg);
}

@media (min-width: 720px) {
  .nav-bar {
    padding: 0.7rem 1.5rem;
  }
}

.flex-grow {
  flex-grow: 1;
}

.nav {
  display: none;
}

@media (min-width: 720px) {
  .nav {
    display: block;
  }
}
</style>
