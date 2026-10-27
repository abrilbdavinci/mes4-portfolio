<script setup>
import SectionHeader from '../common/SectionHeader.vue'
import { profileData } from '../../data/profile.js'
import { FileText, Download } from 'lucide-vue-next'
</script>

<template>
  <section id="cv" class="cv-section">
    <SectionHeader title="Curriculum Vitae" subtitle="Versión textual estructurada para lectura directa y sistemas ATS." />

    <div class="cv-card">
      <div class="cv-preview-info">
        <FileText :size="32" class="cv-file-icon" />
        <div>
          <h3>{{ profileData.name }} - CV Profesional</h3>
          <p>Disponible para descarga en formato PDF estándar optimizado para reclutadores.</p>
        </div>
      </div>
      <a :href="profileData.links.cv" download class="btn-primary">
        <Download :size="18" />
        Descargar CV (PDF)
      </a>
    </div>
  </section>
</template>

<style scoped>
.cv-section {
  margin-bottom: 3rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid var(--color-border);
}

.cv-card {
  background-color: var(--color-card-bg);
  border: 1px solid var(--color-border);
  padding: 1.5rem;
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-subtle);
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 1.5rem;
}

.cv-preview-info {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.cv-file-icon {
  color: var(--color-button);
}

.cv-preview-info h3 {
  font-size: 1.05rem;
  color: var(--color-headline);
}

.cv-preview-info p {
  font-size: 0.85rem;
}
</style>