<script setup lang="ts">
interface ThemeSettings {
  color: string;
  fontSize: number;
  borderRadius: number;
  borderStyle: string;
}

const props = withDefaults(defineProps<{ theme?: ThemeSettings }>(), {
  theme: () => ({
    color: '#000000',
    fontSize: 16,
    borderRadius: 8,
    borderStyle: 'solid'
  })
});
</script>

<template>
  <div 
    class="preview-container"
    :style="{
      '--main-color': theme.color,
      '--font-size': `${theme.fontSize}px`,
      '--border-radius': `${theme.borderRadius}px`,
      '--border-style': theme.borderStyle
    }"
  >
    <h2>Shadow Fiend</h2>
    
    <div class="card">
      <h3>Unleashes the souls of fallen enemies for damage.</h3>
      <p>Capturing Souls from every kill he makes, Shadow Fiend is always gathering his power. Armor fails within the Presence of the Dark Lord, leaving foes no choice but to scramble. Every assault, each carefully aimed Shadowraze kills an enemy, brings him closer to his acme of potency. The Shadow Fiend pauses to charge his demonic energies, then, with a flourish of his lightless wings, unleashes his gathered souls in all directions to obliterate enemies in a howling Requiem of Souls.</p>
      <button class="btn">Shadowraze</button>
    </div>
  </div>
</template>

<style scoped>
.preview-container {
  flex-grow: 1;
  padding: 20px;
  color: var(--main-color);
  font-size: var(--font-size);
}

.card {
  padding: 20px;
  margin-top: 15px;
  border-width: 3px;
  border-color: var(--main-color);
  border-style: var(--border-style);
  border-radius: var(--border-radius);
}

.btn {
  margin-top: 15px;
  padding: 10px 20px;
  background-color: var(--main-color);
  color: #ffffff;
  border: none;
  cursor: pointer;
  font-size: var(--font-size);
  border-radius: var(--border-radius);
  transition: opacity 0.2s ease;
}

.btn:hover {
  opacity: 0.8;
}
</style>