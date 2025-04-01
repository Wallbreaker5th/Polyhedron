<template>
  <div ref="codeContainer">
    <template v-for="(token, index) in finerTokens" :key="index">
      <span
        v-if="token.content !== '\n'"
        :style="{ animationDelay: `${index * 0.02}s` }"
        :class="[token.type, 'word']"
      >
        {{ token.content }}
      </span>
      <br v-else />
    </template>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const props = defineProps({
  code: {
    type: String,
    required: true
  },
  tokens: {
    type: Array,
    required: true
  }
});

const finerTokens = ref([]);

onMounted(() => {
  // Split tokens into finer tokens: split by symbols and whitespace
  props.tokens.forEach(token => {
    const finerTokensArray = token.content.split(/(\s+|\W)/).filter(t => t !== '');
    finerTokens.value.push(...finerTokensArray.map(content => ({ 
      content, 
      type: token.type 
    })));
  });
  
  // Verify token recovery matches original code
  const recoveredCode = finerTokens.value.map(t => t.content).join('');
  console.assert(recoveredCode === props.code, 'Token recovery failed');
  if (recoveredCode !== props.code) {
    let diffIndex = 0;
    while (diffIndex < props.code.length && diffIndex < recoveredCode.length && 
           props.code[diffIndex] === recoveredCode[diffIndex]) {
      diffIndex++;
    }
    const start = Math.max(0, diffIndex - 10);
    const end = diffIndex;
    console.error('Token recovery failed at position', diffIndex, 
                 'Last 10 chars before difference:', props.code.slice(start, end));
  }
});
</script>

<style scoped>
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

.word {
  opacity: 0;
  animation: appear 0.04s forwards;
  display: inline-block;
  white-space: pre;
}
</style>
