<template>
  <div>
    <t-input-number v-model="value" :max="15" :min="-2" :disabled="true" />
  </div>
</template>

<script setup>
import { ref } from 'vue';

const value = ref(3);
</script>
