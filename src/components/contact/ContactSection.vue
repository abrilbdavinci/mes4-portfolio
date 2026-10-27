<script setup>
import { ref } from 'vue'
import SectionHeader from '../common/SectionHeader.vue'
import { profileData } from '../../data/profile.js'
import { Mail, Linkedin, Github, Send } from 'lucide-vue-next'

const form = ref({ name: '', email: '', message: '' })
const submitted = ref(false)

const handleSubmit = () => {
  if (!form.value.name || !form.value.email || !form.value.message) return
  submitted.value = true
}
</script>

<template>
  <section id="contacto" class="contact-section">
    <SectionHeader title="Contacto" subtitle="¿Tenés una propuesta o querés conversar sobre un proyecto? Escribime." />

    <div class="contact-grid">
      <div class="contact-info">
        <h3>Información Directa</h3>
        <p>Siempre abierta a evaluar nuevas oportunidades profesionales en desarrollo frontend y diseño UX/UI.</p>
        
        <div class="contact-links-list">
          <a :href="`mailto:${profileData.email}`" class="contact-link-item">
            <Mail :size="18" />
            <span>{{ profileData.email }}</span>
          </a>
          <a :href="profileData.links.linkedin" target="_blank" rel="noopener" class="contact-link-item">
            <Linkedin :size="18" />
            <span>LinkedIn Profile</span>
          </a>
          <a :href="profileData.links.github" target="_blank" rel="noopener" class="contact-link-item">
            <Github :size="18" />
            <span>GitHub Repository</span>
          </a>
        </div>
      </div>

      <form @submit.prevent="handleSubmit" class="contact-form">
        <div v-if="submitted" class="success-message">
          <p>¡Mensaje preparado! (Simulador de envío). Podes contactarme directamente a través de mi correo electrónico.</p>
        </div>

        <template v-else>
          <div class="form-group">
            <label for="name">Nombre</label>
            <input type="text" id="name" v-model="form.name" required placeholder="Tu nombre" />
          </div>

          <div class="form-group">
            <label for="email">Correo Electrónico</label>
            <input type="email" id="email" v-model="form.email" required placeholder="tu@correo.com" />
          </div>

          <div class="form-group">
            <label for="message">Mensaje</label>
            <textarea id="message" v-model="form.message" rows="4" required placeholder="Escribí tu mensaje aquí..."></textarea>
          </div>

          <button type="submit" class="btn-primary">
            <Send :size="16" />
            Enviar Mensaje
          </button>
        </template>
      </form>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  margin-bottom: 2rem;
}

.contact-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}

.contact-info, .contact-form {
  background-color: var(--color-card-bg);
  border: 1px solid var(--color-border);
  padding: 1.5rem;
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-subtle);
}

.contact-info h3 {
  font-size: 1.1rem;
  color: var(--color-headline);
  margin-bottom: 0.5rem;
}

.contact-info p {
  font-size: 0.85rem;
  margin-bottom: 1.25rem;
}

.contact-links-list {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.contact-link-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  color: var(--color-headline);
  font-size: 0.9rem;
  font-weight: 500;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}

.form-group label {
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--color-headline);
}

.form-group input, .form-group textarea {
  padding: 0.65rem;
  border: 1px solid var(--color-border);
  border-radius: var(--radius-sm);
  font-family: inherit;
  font-size: 0.85rem;
  background-color: var(--color-background);
  color: var(--color-headline);
}

.form-group input:focus, .form-group textarea:focus {
  outline: 2px solid var(--color-button);
}

.success-message {
  padding: 1.5rem;
  background-color: rgba(61, 169, 252, 0.1);
  border-radius: var(--radius-sm);
  color: var(--color-headline);
  font-size: 0.9rem;
  text-align: center;
}
</style>