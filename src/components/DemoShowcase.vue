<template>
  <NomadsShowcase @apply-template="handleApplyTemplate" />
</template>

<script setup lang="ts">
import NomadsShowcase from './NomadsShowcase.vue';

const emit = defineEmits<{
  (e: 'apply-template', payload: { 
    prompt: string; 
    reviewType?: string; 
    reviewTarget?: string; 
    wordCount?: string; 
  }): void;
}>();

function handleApplyTemplate(payload: { 
  prompt: string; 
  reviewType?: string; 
  reviewTarget?: string; 
  wordCount?: string; 
}) {
  emit('apply-template', payload);
}
</script>
