<script setup>
import { ref } from 'vue'
import AppSidebar from './components/layout/AppSidebar.vue'
import ProfileCard from './components/layout/ProfileCard.vue'
import MobileNavigation from './components/layout/MobileNavigation.vue'

import HeroSection from './components/home/HeroSection.vue'
import ProjectGrid from './components/projects/ProjectGrid.vue'
import ExperienceSection from './components/experience/ExperienceSection.vue'
import SkillsSection from './components/skills/SkillsSection.vue'
import EducationSection from './components/education/EducationSection.vue'
import CvSection from './components/cv/CvSection.vue'
import ContactSection from './components/contact/ContactSection.vue'

import SectionHeader from './components/common/SectionHeader.vue'

const activeSection = ref('inicio')

const handleNavigate = (sectionId) => {
  activeSection.value = sectionId
}
</script>

<template>
  <div class="workspace-layout">
    <!-- Sidebar de Navegación -->
    <AppSidebar :activeSection="activeSection" @navigate="handleNavigate" />

    <!-- Contenedor Principal Central y Tarjeta de Perfil -->
    <div class="workspace-main-wrapper">
      

      <main class="workspace-content">
        <HeroSection @navigate="handleNavigate" />
        
        <section id="sobre-mi" class="about-section">
          <SectionHeader title="Sobre mí" subtitle="Perfil profesional y enfoque de trabajo." />
          <div class="about-card">
            <p>
              Soy estudiante de desarrollo web y sistemas multimedia con una fuerte inclinación hacia la creación de interfaces limpias, funcionales y accesibles. Mi enfoque combina el rigor técnico del desarrollo frontend con criterios de diseño UX/UI orientados a resolver problemas reales de los usuarios.
            </p>
          </div>
        </section>

        <ProjectGrid />
        <ExperienceSection />
        <SkillsSection />
        <EducationSection />
        <CvSection />
        <ContactSection />
      </main>
      <ProfileCard />
    </div>

    <!-- Navegación móvil inferior -->
    <MobileNavigation :activeSection="activeSection" @navigate="handleNavigate" />
  </div>
</template>

<style>
@import './assets/styles/global.css';

.workspace-layout {
  display: flex;
  max-width: 1400px;
  margin: 0 auto;
  min-height: 100vh;
}

.workspace-main-wrapper {
  display: flex;
  gap: 2rem;
  padding: 1rem;
  flex: 1;
  align-items: flex-start;
}

.workspace-content {
  flex: 1;
  min-width: 0;
}

.about-section {
  margin-bottom: 3rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid var(--color-border);
}

.about-card {
  background-color: var(--color-card-bg);
  border: 1px solid var(--color-border);
  padding: 1.5rem;
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-subtle);
  font-size: 0.95rem;
  line-height: 1.7;
}

@media (max-width: 1023px) {
  .workspace-main-wrapper {
    flex-direction: column;
    padding: 1rem 1rem 5rem 1rem;
  }
  
  .profile-card {
    width: 100% !important;
    position: static !important;
  }
}
</style>