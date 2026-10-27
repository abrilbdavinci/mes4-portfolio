<script setup>
import SectionHeader from '../common/SectionHeader.vue'
import { profileData } from '../../data/profile.js'
import { ArrowRight, Code2, Layout, Sparkles } from 'lucide-vue-next'

defineEmits(['navigate'])
</script>

<template>
  <section id="inicio" class="hero-section">
    <div class="hero-tag">
      <Sparkles :size="16" />
      <span>Portfolio Profesional & Workspace</span>
    </div>
    
    <h1 class="hero-title">
      Diseño de experiencias digitales y desarrollo web con enfoque analítico.
    </h1>
    
    <p class="hero-description">
      {{ profileData.bio }} Especializada en transformar requerimientos complejos en interfaces limpias, accesibles y optimizadas tanto para usuarios como para sistemas de selección.
    </p>

    <div class="hero-actions">
      <a href="#proyectos" @click="$emit('navigate', 'proyectos')" class="btn-main">
        Explorar Proyectos
        <ArrowRight :size="18" />
      </a>
      <a href="#contacto" @click="$emit('navigate', 'contacto')" class="btn-secondary">
        Contactar
      </a>
    </div>

    <div class="highlights-grid">
      <div class="highlight-card">
        <Layout :size="24" class="highlight-icon" />
        <h3>Diseño UX/UI</h3>
        <p>Interfaces intuitivas, wireframes y sistemas de diseño escalables en Figma.</p>
      </div>
      <div class="highlight-card">
        <Code2 :size="24" class="highlight-icon" />
        <h3>Desarrollo Frontend</h3>
        <p>Aplicaciones reactivas y modulares utilizando Vue 3, Vite y JavaScript moderno.</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  padding: 1rem 0 3rem 0;
  border-bottom: 1px solid var(--color-border);
  margin-bottom: 3rem;
}

.hero-tag {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background-color: rgba(61, 169, 252, 0.1);
  color: var(--color-button);
  padding: 0.35rem 0.75rem;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 600;
  margin-bottom: 1.25rem;
}

.hero-title {
  font-size: 2.25rem;
  color: var(--color-headline);
  margin-bottom: 1rem;
  letter-spacing: -0.02em;
}

.hero-description {
  font-size: 1.05rem;
  color: var(--color-paragraph);
  margin-bottom: 2rem;
  max-width: 650px;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  margin-bottom: 3rem;
}

.btn-main {
  background-color: var(--color-button);
  color: var(--color-button-text);
  padding: 0.75rem 1.25rem;
  border-radius: var(--radius-sm);
  font-weight: 600;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  transition: opacity 0.2s;
}

.btn-main:hover {
  opacity: 0.9;
  color: var(--color-button-text);
}

.btn-secondary {
  background-color: rgba(144, 180, 206, 0.15);
  color: var(--color-headline);
  padding: 0.75rem 1.25rem;
  border-radius: var(--radius-sm);
  font-weight: 600;
  transition: background-color 0.2s;
}

.btn-secondary:hover {
  background-color: rgba(144, 180, 206, 0.3);
  color: var(--color-headline);
}

.highlights-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 1.25rem;
}

.highlight-card {
  background-color: var(--color-card-bg);
  border: 1px solid var(--color-border);
  padding: 1.25rem;
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-subtle);
}

.highlight-icon {
  color: var(--color-button);
  margin-bottom: 0.75rem;
}

.highlight-card h3 {
  font-size: 1.05rem;
  margin-bottom: 0.35rem;
}

.highlight-card p {
  font-size: 0.85rem;
}
</style>