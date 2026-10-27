<script setup>
import SectionHeader from '../common/SectionHeader.vue'
import { skillsData } from '../../data/skills.js'
import { CheckCircle2 } from 'lucide-vue-next'
</script>

<template>
  <section id="habilidades" class="skills-section">
    <SectionHeader title="Habilidades y Competencias" subtitle="Competencias técnicas organizadas por áreas de especialización." />

    <div class="skills-grid">
      <div v-for="(group, index) in skillsData" :key="index" class="skill-group-card">
        <h3>{{ group.category }}</h3>
        <ul class="skills-list">
          <li v-for="(skill, sIdx) in group.skills" :key="sIdx" class="skill-item">
            <CheckCircle2 :size="16" class="skill-check" />
            <span>{{ skill }}</span>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills-section {
  margin-bottom: 3rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid var(--color-border);
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 1.25rem;
}

.skill-group-card {
  background-color: var(--color-card-bg);
  border: 1px solid var(--color-border);
  padding: 1.25rem;
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-subtle);
}

.skill-group-card h3 {
  font-size: 1.05rem;
  color: var(--color-headline);
  margin-bottom: 1rem;
  padding-bottom: 0.5rem;
  border-bottom: 1px solid var(--color-border);
}

.skills-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.skill-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.85rem;
  color: var(--color-paragraph);
}

.skill-check {
  color: var(--color-button);
}
</style>