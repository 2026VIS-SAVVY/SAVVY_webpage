<template>
  <section class="hero-wrap">
    <!-- White title card: title + nav only -->
    <div class="hero-card">
      <h1 class="paper-title">
        SAVVY: Student Attention Visualization for Video-based Learning Analysis
      </h1>
      <nav class="hero-nav">
        <a v-for="link in navLinks" :key="link.href" :href="link.href" class="nav-link">
          {{ link.label }}
        </a>
      </nav>
    </div>

    <!-- Image placeholder area: same width as card, directly below it -->
    <div class="hero-img-wrap">
      <div class="hero-img-ph">
        <svg viewBox="0 0 48 48" fill="none" stroke="currentColor" stroke-width="1.5" class="img-ph-icon">
          <rect x="4" y="8" width="40" height="32" rx="3"/>
          <circle cx="16" cy="20" r="4"/>
          <path d="M4 32 l10-8 8 6 8-10 14 12"/>
        </svg>
        <span class="img-ph-label">Paper Figure / System Overview</span>
        <span class="img-ph-hint">Replace with your paper's figure (e.g., system architecture, pipeline overview)</span>
      </div>
    </div>
  </section>
</template>

<script setup>
const navLinks = [
  { href: '#teaser',     label: 'Teaser' },
  { href: '#abstract',   label: 'Abstract' },
  { href: '#video',      label: 'Video' },
  { href: '#dataset',    label: 'Dataset' },
  { href: '#code',       label: 'Code' },
  { href: '#references', label: 'References' },
]
</script>

<style scoped>
/* Outer section: gradient bg, column flex so card and img-wrap stack */
.hero-wrap {
  width: 100%;
  box-sizing: border-box;
  background: linear-gradient(150deg, #13131f 0%, #16213e 55%, #0f3460 100%);
  padding: clamp(32px, 6vw, 60px) clamp(16px, 4vw, 24px) clamp(28px, 5vw, 52px);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0;
}

/* White title card */
.hero-card {
  background: #ffffff;
  border-radius: 20px 20px 0 0;
  padding: clamp(28px, 5vw, 52px) clamp(20px, 6vw, 56px) clamp(24px, 4vw, 44px);
  max-width: 1100px;
  width: 100%;
  text-align: center;
  box-shadow: 0 4px 0 rgba(0,0,0,.15);
}

.paper-title {
  font-family: Arial, sans-serif;
  font-size: clamp(1.4rem, 3.2vw, 2.2rem);
  font-weight: 700;
  color: #111827;
  line-height: 1.35;
  margin-bottom: 28px;
  white-space: normal;
  word-break: keep-all;
  overflow-wrap: break-word;
}

.hero-nav {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 8px;
}

.nav-link {
  display: inline-block;
  padding: 8px 16px;
  border: 1.5px solid #d1d5db;
  border-radius: 6px;
  color: #333333;
  background-color: #ffffff;
  font-family: Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  text-decoration: none;
  transition: all 0.3s;
  white-space: nowrap;
  position: relative;
  box-shadow: 0 1px 4px rgba(0,0,0,0.10), 0 0.5px 1.5px rgba(0,0,0,0.07);
}
.nav-link::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 2px;
  background-color: #42b883;
  transition: width 0.3s;
}
.nav-link:hover {
  background-color: #ffffff;
  color: #000000;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  border-color: #42b883;
  transform: translateY(-2px);
}
.nav-link:hover::after {
  width: 100%;
}

/* Image area: same max-width as card, flush below it, rounded bottom */
.hero-img-wrap {
  max-width: 1100px;
  width: 100%;
  border-radius: 0 0 20px 20px;
  overflow: hidden;
  box-shadow: 0 8px 40px rgba(0,0,0,.45);
}

.hero-img-ph {
  width: 100%;
  min-height: clamp(200px, 30vw, 420px);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
  background: #f3f4f6;
  color: #9ca3af;
  padding: 2.5rem 1rem;
  border-top: 1px solid #e5e7eb;
  box-sizing: border-box;
}

.img-ph-icon {
  width: clamp(40px, 6vw, 52px);
  height: clamp(40px, 6vw, 52px);
  opacity: 0.38;
  margin-bottom: 4px;
}
.img-ph-label {
  font-family: Arial, sans-serif;
  font-size: clamp(0.85rem, 2vw, 1rem);
  font-weight: 600;
  color: #6b7280;
}
.img-ph-hint {
  font-family: Arial, sans-serif;
  font-size: clamp(0.75rem, 1.8vw, 0.85rem);
  color: #9ca3af;
  max-width: 400px;
  line-height: 1.5;
  text-align: center;
}

@media (max-width: 480px) {
  .hero-card { border-radius: 14px 14px 0 0; }
  .hero-img-wrap { border-radius: 0 0 14px 14px; }
}
</style>
