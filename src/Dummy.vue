<template>
  <div>
    <span v-for="(word, index) in words" :key="index" :style="{ animationDelay: `${index * 0.02}s` }" class="word">
      {{ word }}&nbsp;
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.'
    }
  },
  computed: {
    words() {
      return this.text.split(' ')
    }
  }
}
</script>

<style scoped>
.word {
  opacity: 0;
  animation: appear 0.04s forwards;
  display: inline-block;
}

@keyframes appear {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
