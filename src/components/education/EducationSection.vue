<script setup>
import SectionHeader from '../common/SectionHeader.vue'
import { educationData } from '../../data/education.js'
import { GraduationCap, Calendar } from 'lucide-vue-next'
</script>

<template>
  <section id="formacion" class="education-section">
    <SectionHeader title="Formación Académica" subtitle="Estudios formales y capacitación continua." />

    <div class="education-grid">
      <div v-for="edu in educationData" :key="edu.id" class="education-card">
        <div class="edu-icon">
          <GraduationCap :size="20" />
        </div>
        <div class="edu-content">
          <h3>{{ edu.degree }}</h3>
          <span class="institution">{{ edu.institution }}</span>
          <div class="edu-meta">
            <span class="period"><Calendar :size="14" /> {{ edu.period }}</span>
            <span class="status-badge">{{ edu.status }}</span>
          </div>
          <p>{{ edu.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.education-section {
  margin-bottom: 3rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid var(--color-border);
}

.education-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.25rem;
}

.education-card {
  background-color: var(--color-card-bg);
  border: 1px solid var(--color-border);
  padding: 1.25rem;
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-subtle);
  display: flex;
  gap: 1rem;
}

.edu-icon {
  background-color: rgba(61, 169, 252, 0.1);
  color: var(--color-button);
  width: 40px;
  height: 40px;
  border-radius: var(--radius-sm);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.edu-content h3 {
  font-size: 1.05rem;
  color: var(--color-headline);
}

.institution {
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--color-button);
  display: block;
  margin-bottom: 0.35rem;
}

.edu-meta {
  display: flex;
  gap: 1rem;
  font-size: 0.8rem;
  color: var(--color-paragraph);
  margin-bottom: 0.5rem;
  align-items: center;
}

.period {
  display: flex;
  align-items: center;
  gap: 0.3rem;
}

.status-badge {
  background-color: rgba(144, 180, 206, 0.2);
  padding: 0.1rem 0.4rem;
  border-radius: 4px;
  font-weight: 500;
}

.edu-content p {
  font-size: 0.85rem;
}
</style>