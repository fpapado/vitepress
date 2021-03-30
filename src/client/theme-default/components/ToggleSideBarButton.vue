<template>
  <button
    class="sidebar-button" 
    :aria-expanded="open"
    @click="$emit('toggle')"
  >
    <svg
      class="icon"
      xmlns="http://www.w3.org/2000/svg"
      aria-label="Menu"
      role="img"
      focusable="false"
      viewBox="0 0 448 512"
    >
      <path
        fill="currentColor"
        d="M436 124H12c-6.627 0-12-5.373-12-12V80c0-6.627 5.373-12 12-12h424c6.627 0 12 5.373 12 12v32c0 6.627-5.373 12-12 12zm0 160H12c-6.627 0-12-5.373-12-12v-32c0-6.627 5.373-12 12-12h424c6.627 0 12 5.373 12 12v32c0 6.627-5.373 12-12 12zm0 160H12c-6.627 0-12-5.373-12-12v-32c0-6.627 5.373-12 12-12h424c6.627 0 12 5.373 12 12v32c0 6.627-5.373 12-12 12z"
        class
      />
    </svg>
  </button>
</template>

<script>
export default {
  props: {
    open: { type: Boolean, required: true }
  },
  emits: ['toggle']
}
</script>

<style>
.sidebar-button {
  position: absolute;
  top: 0.6rem;
  left: 1rem;
  display: none;
  margin: 0;
  padding: 0.6rem;
  cursor: pointer;
  border: none;
  background: none;
}

.sidebar-button .icon {
  display: block;
  width: 1.25rem;
  height: 1.25rem;
}

@media screen and (max-width: 719px) {
  .sidebar-button {
    display: block;
  }
}
</style>
