<script setup>
import { profileData } from '../../data/profile.js'
import { MapPin, Mail, Phone, Clock, Linkedin, Github, Download, CheckCircle2 } from 'lucide-vue-next'
</script>

<template>
  <aside class="profile-card" aria-label="Tarjeta de presentación personal">
    <div class="profile-header">
      <div class="avatar-container">
        <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=400&q=80" :alt="profileData.name" class="profile-avatar" />
      </div>
      <h1 class="profile-name">{{ profileData.name }}</h1>
      <p class="profile-role">{{ profileData.role }}</p>
    </div>

    <div class="profile-meta">
      <div class="meta-item">
        <MapPin :size="16" class="meta-icon" />
        <span>{{ profileData.location }}</span>
      </div>
      <div class="meta-item">
        <Mail :size="16" class="meta-icon" />
        <a :href="`mailto:${profileData.email}`" class="meta-link">{{ profileData.email }}</a>
      </div>
      <div class="meta-item" v-if="profileData.phone">
        <Phone :size="16" class="meta-icon" />
        <a :href="`tel:${profileData.phone.replace(/\s+/g, '')}`" class="meta-link">{{ profileData.phone }}</a>
      </div>
      <div class="meta-item">
        <Clock :size="16" class="meta-icon" />
        <span>{{ profileData.schedule }}</span>
      </div>
      <div class="meta-item availability">
        <CheckCircle2 :size="16" class="status-icon" />
        <span>{{ profileData.availability }}</span>
      </div>
    </div>


    <div class="profile-actions">
      <a :href="profileData.links.cv" download class="btn-primary">
        <Download :size="18" />
        Descargar CV
      </a>
      <div class="social-links">
        <a :href="profileData.links.linkedin" target="_blank" rel="noopener" aria-label="LinkedIn">
          <Linkedin :size="20" />
        </a>
        <a :href="profileData.links.github" target="_blank" rel="noopener" aria-label="GitHub">
          <Github :size="20" />
        </a>
      </div>
    </div>
  </aside>
</template>

<style scoped>
.profile-card {
  width: 280px;
  background-color: var(--color-card-bg);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  padding: 1.5rem;
  height: fit-content;
  position: sticky;
  top: 2rem;
  box-shadow: var(--shadow-subtle);
}

.profile-header {
  text-align: center;
  margin-bottom: 1.25rem;
}

.avatar-container {
  width: 90px;
  height: 90px;
  margin: 0 auto 1rem auto;
  border-radius: 50%;
  overflow: hidden;
  border: 2px solid var(--color-headline);
}

.profile-avatar {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.profile-name {
  font-size: 1.2rem;
  color: var(--color-headline);
  margin-bottom: 0.25rem;
}

.profile-role {
  font-size: 0.85rem;
  color: var(--color-paragraph);
  font-weight: 500;
}

.profile-meta {
  font-size: 0.8rem;
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  margin-bottom: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid var(--color-border);
}

.meta-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--color-paragraph);
  word-break: break-all;
}

.meta-icon {
  color: var(--color-button);
  flex-shrink: 0;
}

.meta-link {
  color: var(--color-paragraph);
  transition: color 0.2s ease;
}

.meta-link:hover {
  color: var(--color-headline);
  text-decoration: underline;
}

.status-icon {
  color: #2e7d32;
  flex-shrink: 0;
}

.profile-specialties {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  margin-bottom: 1.5rem;
}

.specialty-tag {
  background-color: rgba(144, 180, 206, 0.15);
  color: var(--color-headline);
  font-size: 0.7rem;
  padding: 0.2rem 0.5rem;
  border-radius: var(--radius-sm);
  font-weight: 500;
}

.profile-actions {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.btn-primary {
  background-color: var(--color-button);
  color: var(--color-button-text);
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.75rem;
  border-radius: var(--radius-sm);
  font-size: 0.9rem;
  font-weight: 600;
  transition: opacity 0.2s ease;
}

.btn-primary:hover {
  opacity: 0.9;
  color: var(--color-button-text);
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 1rem;
  color: var(--color-headline);
}
</style>