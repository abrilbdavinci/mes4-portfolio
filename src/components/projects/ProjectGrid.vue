<script setup>
import { ref, computed } from 'vue'
import { projectsData } from '../../data/projects.js'
import ProjectCard from './ProjectCard.vue'
import SectionHeader from '../common/SectionHeader.vue'
import { ExternalLink, X } from 'lucide-vue-next'

const selectedCategory = ref('todos')
const selectedProject = ref(null)

const categories = [
  { id: 'todos', label: 'Todos' },
  { id: 'ux-ui', label: 'UX/UI' },
  { id: 'frontend', label: 'Frontend' },
  { id: 'full-stack', label: 'Full-Stack' }
]

const filteredProjects = computed(() => {
  if (selectedCategory.value === 'todos') return projectsData
  return projectsData.filter(p => p.category === selectedCategory.value)
})

const openModal = (project) => {
  selectedProject.value = project
}

const closeModal = () => {
  selectedProject.value = null
}
</script>

<template>
  <section id="proyectos" class="projects-section">
    <SectionHeader title="Proyectos Destacados" subtitle="Trabajos recientes en desarrollo web, interfaces y diseño UX/UI." />

    <div class="filters-container">
      <button 
        v-for="cat in categories" 
        :key="cat.id"
        :class="['filter-btn', { active: selectedCategory === cat.id }]"
        @click="selectedCategory = cat.id"
      >
        {{ cat.label }}
      </button>
    </div>

    <div class="projects-grid">
      <ProjectCard 
        v-for="project in filteredProjects" 
        :key="project.id" 
        :project="project" 
        @select="openModal"
      />
    </div>

    <div v-if="filteredProjects.length === 0" class="empty-state">
      <p>No se encontraron proyectos en esta categoría.</p>
    </div>

    <!-- Modal de detalle de proyecto -->
    <div v-if="selectedProject" class="modal-backdrop" @click.self="closeModal">
      <div class="modal-content">
        <button class="modal-close" @click="closeModal" aria-label="Cerrar detalle">
          <X :size="20" />
        </button>
        
        <div class="modal-header">
          <span class="modal-category">{{ selectedProject.category }}</span>
          <h2>{{ selectedProject.title }}</h2>
          <p class="modal-role"><strong>Rol:</strong> {{ selectedProject.role }}</p>
        </div>

        <div class="modal-body">
          <div class="modal-image-container">
            <img :src="selectedProject.image" :alt="selectedProject.title" />
          </div>

          <div class="modal-details-grid">
            <div>
              <h4>Contexto</h4>
              <p>{{ selectedProject.context }}</p>
            </div>
            <div>
              <h4>Desafío</h4>
              <p>{{ selectedProject.challenge }}</p>
            </div>
            <div>
              <h4>Solución</h4>
              <p>{{ selectedProject.solution }}</p>
            </div>
          </div>

          <div class="modal-techs">
            <h4>Tecnologías utilizadas</h4>
            <div class="tech-tags">
              <span v-for="(t, i) in selectedProject.technologies" :key="i" class="tech-tag">{{ t }}</span>
            </div>
          </div>

          <div class="modal-links" v-if="selectedProject.links">
            <a v-if="selectedProject.links.demo" :href="selectedProject.links.demo" target="_blank" rel="noopener" class="btn-primary">
              Ver Demo <ExternalLink :size="16" />
            </a>
            <a v-if="selectedProject.links.repository" :href="selectedProject.links.repository" target="_blank" rel="noopener" class="btn-secondary">
              Ver Repositorio
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  margin-bottom: 3rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid var(--color-border);
}

.filters-container {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
}

.filter-btn {
  background-color: rgba(144, 180, 206, 0.15);
  color: var(--color-paragraph);
  padding: 0.4rem 0.85rem;
  border-radius: var(--radius-sm);
  font-size: 0.85rem;
  font-weight: 500;
  transition: all 0.2s;
}

.filter-btn:hover {
  background-color: rgba(144, 180, 206, 0.3);
  color: var(--color-headline);
}

.filter-btn.active {
  background-color: var(--color-headline);
  color: var(--color-background);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 1.25rem;
}

.empty-state {
  text-align: center;
  padding: 2rem;
  color: var(--color-paragraph);
}

/* Estilos del Modal */
.modal-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(9, 64, 103, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
  padding: 1rem;
}

.modal-content {
  background-color: var(--color-background);
  border-radius: var(--radius-md);
  max-width: 650px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  padding: 2rem;
  position: relative;
  box-shadow: 0 10px 30px rgba(9, 64, 103, 0.2);
}

.modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  color: var(--color-paragraph);
  cursor: pointer;
}

.modal-header {
  margin-bottom: 1.25rem;
}

.modal-category {
  font-size: 0.75rem;
  text-transform: uppercase;
  color: var(--color-button);
  font-weight: 700;
}

.modal-header h2 {
  font-size: 1.5rem;
  margin: 0.25rem 0;
}

.modal-role {
  font-size: 0.85rem;
  color: var(--color-paragraph);
}

.modal-image-container {
  height: 240px;
  border-radius: var(--radius-sm);
  overflow: hidden;
  margin-bottom: 1.25rem;
}

.modal-image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.modal-details-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
  margin-bottom: 1.25rem;
  font-size: 0.9rem;
}

.modal-details-grid h4 {
  font-size: 0.95rem;
  color: var(--color-headline);
  margin-bottom: 0.2rem;
}

.modal-techs {
  margin-bottom: 1.5rem;
}

.modal-techs h4 {
  font-size: 0.95rem;
  margin-bottom: 0.5rem;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
}

.modal-links {
  display: flex;
  gap: 1rem;
}
</style>