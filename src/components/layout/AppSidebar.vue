<script setup>
import { computed } from 'vue'
import { Home, User, Briefcase, Code, Cpu, GraduationCap, FileText, Mail } from 'lucide-vue-next'
import { translations } from '../../data/i18n.js'

const props = defineProps({
  activeSection: {
    type: String,
    required: true
  },
  currentLang: {
    type: String,
    required: true,
    default: 'es'
  }
})

const emit = defineEmits(['navigate', 'change-lang'])

// Validación segura para evitar que falle si translations o el idioma no cargan
const t = computed(() => {
  if (translations && translations[props.currentLang]) {
    return translations[props.currentLang].nav
  }
  return {
    inicio: "Inicio",
    sobreMi: "Sobre mí",
    proyectos: "Proyectos",
    experiencia: "Experiencia",
    habilidades: "Habilidades",
    formacion: "Formación",
    cv: "CV",
    contacto: "Contacto"
  }
})

const navItems = computed(() => [
  { id: 'inicio', label: t.value.inicio, icon: Home },
  { id: 'sobre-mi', label: t.value.sobreMi, icon: User },
  { id: 'proyectos', label: t.value.proyectos, icon: Briefcase },
  { id: 'experiencia', label: t.value.experiencia, icon: Code },
  { id: 'habilidades', label: t.value.habilidades, icon: Cpu },
  { id: 'formacion', label: t.value.formacion, icon: GraduationCap },
  { id: 'cv', label: t.value.cv, icon: FileText },
  { id: 'contacto', label: t.value.contacto, icon: Mail },
])
</script>

<template>
  <nav class="sidebar" aria-label="Navegación principal">
    <!-- Selector de Idioma con Banderas -->
    <div class="language-selector">
      <button 
        :class="['lang-btn', { active: currentLang === 'es' }]" 
        @click="$emit('change-lang', 'es')"
        title="Español"
        aria-label="Cambiar a Español"
      >
        <span class="flag-icon">🇪🇸</span>
        <span class="lang-text">ES</span>
      </button>
      <button 
        :class="['lang-btn', { active: currentLang === 'en' }]" 
        @click="$emit('change-lang', 'en')"
        title="English"
        aria-label="Switch to English"
      >
        <span class="flag-icon">🇬🇧</span>
        <span class="lang-text">EN</span>
      </button>
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
  padding: 1.5rem 1rem;
  position: sticky;
  top: 0;
  height: 100vh;
}

.language-selector {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 2rem;
  padding-left: 0.5rem;
}

.lang-btn {
  background: none;
  border: 1px solid var(--color-border);
  border-radius: var(--radius-sm);
  padding: 0.35rem 0.5rem;
  display: flex;
  align-items: center;
  gap: 0.35rem;
  cursor: pointer;
  font-size: 0.75rem;
  font-weight: 600;
  color: var(--color-paragraph);
  transition: all 0.2s ease;
}

.lang-btn:hover {
  background-color: rgba(144, 180, 206, 0.1);
  color: var(--color-headline);
}

.lang-btn.active {
  border-color: var(--color-button);
  background-color: rgba(61, 169, 252, 0.1);
  color: var(--color-headline);
}

.flag-icon {
  font-size: 1rem;
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