<script setup lang="ts">
import { ref } from 'vue';
import ThemeManager from './components/ThemeManager.vue';
import Preview from './components/Preview.vue';

interface ThemeSettings {
  color: string;
  fontSize: number;
  borderRadius: number;
  borderStyle: string;
}

const theme = ref<ThemeSettings>({
  color: '#000000',
  fontSize: 16,
  borderRadius: 8,
  borderStyle: 'solid'
});

const handleThemeUpdate = (newTheme: ThemeSettings) => {
  theme.value = newTheme;
};
</script>

<template>
  <div class="app-container">
    <ThemeManager :theme="theme" @updateTheme="handleThemeUpdate" />
    <Preview :theme="theme" />
  </div>
</template>

<style scoped>
.app-container {
  display: flex;
  gap: 30px;
  padding: 20px;
  font-family: sans-serif;
}
</style>