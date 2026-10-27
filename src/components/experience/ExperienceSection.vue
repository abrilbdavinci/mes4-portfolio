<script setup>
import SectionHeader from '../common/SectionHeader.vue'
import { experienceData } from '../../data/experience.js'
import { Briefcase, Calendar } from 'lucide-vue-next'
</script>

<template>
  <section id="experiencia" class="experience-section">
    <SectionHeader title="Experiencia Profesional" subtitle="Trayectoria laboral, freelance y proyectos independientes." />

    <div class="experience-timeline">
      <div v-for="exp in experienceData" :key="exp.id" class="experience-item">
        <div class="experience-marker">
          <Briefcase :size="16" />
        </div>
        <div class="experience-content">
          <div class="experience-header">
            <h3>{{ exp.role }}</h3>
            <span class="company-name">{{ exp.company }}</span>
          </div>
          <div class="experience-meta">
            <span class="period"><Calendar :size="14" /> {{ exp.period }}</span>
            <span class="modality-badge">{{ exp.modality }}</span>
          </div>
          <p class="experience-desc">{{ exp.description }}</p>
          <div class="experience-techs">
            <span v-for="(t, i) in exp.technologies" :key="i" class="tech-tag">{{ t }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.experience-section {
  margin-bottom: 3rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid var(--color-border);
}

.experience-timeline {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  position: relative;
  padding-left: 1.5rem;
  border-left: 2px solid var(--color-border);
}

.experience-item {
  position: relative;
}

.experience-marker {
  position: absolute;
  left: -1.95rem;
  top: 0;
  width: 28px;
  height: 28px;
  background-color: var(--color-button);
  color: var(--color-button-text);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 0 0 4px var(--color-background);
}

.experience-content {
  background-color: var(--color-card-bg);
  border: 1px solid var(--color-border);
  padding: 1.25rem;
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-subtle);
}

.experience-header h3 {
  font-size: 1.1rem;
  color: var(--color-headline);
}

.company-name {
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--color-button);
  display: block;
  margin-bottom: 0.5rem;
}

.experience-meta {
  display: flex;
  gap: 1rem;
  font-size: 0.8rem;
  color: var(--color-paragraph);
  margin-bottom: 0.75rem;
  align-items: center;
}

.period {
  display: flex;
  align-items: center;
  gap: 0.3rem;
}

.modality-badge {
  background-color: rgba(144, 180, 206, 0.2);
  padding: 0.1rem 0.4rem;
  border-radius: 4px;
  font-weight: 500;
}

.experience-desc {
  font-size: 0.85rem;
  margin-bottom: 0.75rem;
}

.experience-techs {
  display: flex;
  flex-wrap: wrap;
  gap: 0.35rem;
}
</style>