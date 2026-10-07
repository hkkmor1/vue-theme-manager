<script setup lang="ts">
interface ThemeSettings {
  color: string;
  fontSize: number;
  borderRadius: number;
  borderStyle: string;
}

const props = defineProps<{ 
  theme: ThemeSettings 
}>();

const emit = defineEmits<{
  (e: 'updateTheme', payload: ThemeSettings): void
}>();

const onColorChange = (event: Event) => {
  const target = event.target as HTMLInputElement;
  emit('updateTheme', { ...props.theme, color: target.value });
};

const onFontSizeChange = (event: Event) => {
  const target = event.target as HTMLInputElement;
  emit('updateTheme', { ...props.theme, fontSize: Number(target.value) });
};

const onBorderRadiusChange = (event: Event) => {
  const target = event.target as HTMLInputElement;
  emit('updateTheme', { ...props.theme, borderRadius: Number(target.value) });
};

const onBorderStyleChange = (event: Event) => {
  const target = event.target as HTMLSelectElement;
  emit('updateTheme', { ...props.theme, borderStyle: target.value });
};
</script>

<template>
  <div class="manager">
    <h2>Налаштування теми</h2>
    
    <div class="control-group">
      <label>Колір елементів:</label>
      <input 
        type="color" 
        :value="theme.color" 
        @input="onColorChange" 
      />
    </div>

    <div class="control-group">
      <label>Розмір шрифту (px):</label>
      <input 
        type="range" 
        min="14" max="32" 
        :value="theme.fontSize" 
        @input="onFontSizeChange" 
      />
    </div>

    <div class="control-group">
      <label>Заокруглення (px):</label>
      <input 
        type="range" 
        min="0" max="50" 
        :value="theme.borderRadius" 
        @input="onBorderRadiusChange" 
      />
    </div>

    <div class="control-group">
      <label>Стиль рамки:</label>
      <select :value="theme.borderStyle" @change="onBorderStyleChange">
        <option value="solid">solid</option>
        <option value="dashed">dashed</option>
        <option value="dotted">dotted</option>
      </select>
    </div>
  </div>
</template>

<style scoped>
.manager {
  width: 300px;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
}
.control-group {
  margin-bottom: 15px;
  display: flex;
  flex-direction: column;
  gap: 5px;
}
</style>