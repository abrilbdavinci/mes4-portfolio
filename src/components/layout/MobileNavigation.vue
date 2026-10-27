<script setup>
import { Home, User, Briefcase, Code, Cpu, GraduationCap, FileText, Mail } from 'lucide-vue-next'

defineProps({
  activeSection: { type: String, required: true }
})

defineEmits(['navigate'])

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
  <nav class="mobile-nav" aria-label="Navegación móvil">
    <a 
      v-for="item in navItems" 
      :key="item.id"
      :href="`#${item.id}`"
      :class="['mobile-nav-link', { active: activeSection === item.id }]"
      @click="$emit('navigate', item.id)"
      :aria-label="item.label"
    >
      <component :is="item.icon" :size="20" />
    </a>
  </nav>
</template>

<style scoped>
.mobile-nav {
  display: none;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: var(--color-background);
  border-top: 1px solid var(--color-border);
  padding: 0.5rem 1rem;
  justify-content: space-around;
  z-index: 1000;
  box-shadow: 0 -4px 10px rgba(9, 64, 103, 0.05);
}

.mobile-nav-link {
  color: var(--color-paragraph);
  padding: 0.5rem;
  border-radius: var(--radius-sm);
  display: flex;
  align-items: center;
  justify-content: center;
}

.mobile-nav-link.active {
  color: var(--color-button);
  background-color: rgba(61, 169, 252, 0.1);
}

@media (max-width: 1023px) {
  .mobile-nav {
    display: flex;
  }
}
</style>