<template>
  <!-- 
    NOTE: the inert attribute correctly hides the sidebar from
    assistive technologies, both as information and in the tab order.
    This avoids users getting stuck on a hidden list of links when
    the menu is shown but collapsed.
    Because we animate the menu, we cannot hide it completely with
    display: none, and thus must rely on inert instead.
  -->
  <nav class="sidebar" :class="{ open }" :inert="!open">
    <NavLinks class="nav" />

    <slot name="sidebar-top" />

    <SideBarLinks />

    <slot name="sidebar-bottom" />
  </nav>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'
import NavLinks from './NavLinks.vue'
import SideBarLinks from './SideBarLinks.vue'

defineProps({
  open: { type: Boolean, required: true }
})
</script>

<style scoped>
.sidebar {
  position: fixed;
  top: var(--header-height);
  bottom: 0;
  left: 0;
  z-index: var(--z-index-sidebar);
  border-right: 1px solid var(--c-divider);
  width: 16.4rem;
  background-color: var(--c-bg);
  overflow-y: auto;
  transform: translateX(-100%);
  transition: transform 0.25s ease;
}

@media (min-width: 720px) {
  .sidebar {
    transform: translateX(0);
  }
}

@media (min-width: 960px) {
  .sidebar {
    width: 20rem;
  }
}

.sidebar.open {
  transform: translateX(0);
}

.nav {
  display: block;
}

@media (min-width: 720px) {
  .nav {
    display: none;
  }
}
</style>
