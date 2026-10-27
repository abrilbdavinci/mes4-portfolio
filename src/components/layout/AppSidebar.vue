<script setup>
import { ref } from 'vue'
import { Home, User, Briefcase, Code, Cpu, GraduationCap, FileText, Mail } from 'lucide-vue-next'

const props = defineProps({
  activeSection: {
    type: String,
    required: true
  }
})

const emit = defineEmits(['navigate'])

const navItems = [
  { id: 'inicio', label: 'Inicio', icon: Home },
  { id: 'sobre-mi', label: 'Sobre mí', icon: User },
  { id: 'proyectos', label: 'Proyectos', icon: Briefcase },
  { id: 'experiencia', label: 'Experiencia', icon: Code },
  { id: 'habilidades', label: 'Habilidades', icon: Cpu },
  { id: 'formacion', label: 'Formación', icon: GraduationCap },
  { id: 'cv', label: 'CV', icon: FileText },
  { id: 'contacto', label: 'Contacto', icon: Mail },
]
</script>

<template>
  <nav class="sidebar" aria-label="Navegación principal">
    <div class="sidebar-brand">
      <span class="brand-badge">AB</span>
    </div>
    
    <ul class="sidebar-menu">
      <li v-for="item in navItems" :key="item.id">
        <a 
          :href="`#${item.id}`"
          :class="['sidebar-link', { active: activeSection === item.id }]"
          @click="$emit('navigate', item.id)"
        >
          <component :is="item.icon" class="sidebar-icon" :size="20" />
          <span class="sidebar-label">{{ item.label }}</span>
        </a>
      </li>
    </ul>
  </nav>
</template>

<style scoped>
.sidebar {
  width: 200px;
  background-color: var(--color-background);
  border-right: 1px solid var(--color-border);
  display: flex;
  flex-direction: column;
  padding: 2rem 1rem;
  position: sticky;
  top: 0;
  height: 100vh;
}

.sidebar-brand {
  margin-bottom: 2.5rem;
  padding-left: 0.75rem;
}

.brand-badge {
  background-color: var(--color-headline);
  color: var(--color-background);
  font-weight: 800;
  padding: 0.5rem 0.75rem;
  border-radius: var(--radius-sm);
  font-size: 1.1rem;
}

.sidebar-menu {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.sidebar-link {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem;
  border-radius: var(--radius-sm);
  color: var(--color-paragraph);
  font-weight: 500;
  font-size: 0.95rem;
  transition: all 0.2s ease;
}

.sidebar-link:hover {
  background-color: rgba(144, 180, 206, 0.1);
  color: var(--color-headline);
}

.sidebar-link.active {
  background-color: var(--color-button);
  color: var(--color-button-text);
}
</style>