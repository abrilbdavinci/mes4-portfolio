<script setup>
import { ExternalLink, Github } from 'lucide-vue-next'

defineProps({
  project: { type: Object, required: true }
})

defineEmits(['select'])
</script>

<template>
  <article class="project-card" @click="$emit('select', project)">
    <div class="project-image-container">
      <img :src="project.image" :alt="project.title" class="project-image" loading="lazy" />
      <span class="project-category-badge">{{ project.category }}</span>
    </div>
    
    <div class="project-content">
      <h3 class="project-title">{{ project.title }}</h3>
      <p class="project-description">{{ project.description }}</p>
      
      <div class="project-techs">
        <span v-for="(tech, index) in project.technologies" :key="index" class="tech-tag">
          {{ tech }}
        </span>
      </div>
    </div>
  </article>
</template>

<style scoped>
.project-card {
  background-color: var(--color-card-bg);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  overflow: hidden;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  box-shadow: var(--shadow-subtle);
  display: flex;
  flex-direction: column;
}

.project-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 24px rgba(9, 64, 103, 0.08);
}

.project-image-container {
  height: 180px;
  position: relative;
  overflow: hidden;
}

.project-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.project-card:hover .project-image {
  transform: scale(1.03);
}

.project-category-badge {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: var(--color-headline);
  color: var(--color-background);
  font-size: 0.7rem;
  font-weight: 600;
  padding: 0.25rem 0.5rem;
  border-radius: var(--radius-sm);
  text-transform: uppercase;
}

.project-content {
  padding: 1.25rem;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.project-title {
  font-size: 1.1rem;
  color: var(--color-headline);
  margin-bottom: 0.5rem;
}

.project-description {
  font-size: 0.85rem;
  color: var(--color-paragraph);
  margin-bottom: 1rem;
  flex-grow: 1;
}

.project-techs {
  display: flex;
  flex-wrap: wrap;
  gap: 0.35rem;
}

.tech-tag {
  background-color: rgba(144, 180, 206, 0.15);
  color: var(--color-headline);
  font-size: 0.7rem;
  padding: 0.15rem 0.4rem;
  border-radius: 4px;
  font-weight: 500;
}
</style>