<template>
  <section id="home" class="hero">
    <div class="container hero-content">
      <div class="hero-text">
        <div class="greeting">
          <span class="wave">👋</span>
          <span>Hi, I'm</span>
        </div>
        <h1 class="hero-title">
          <span class="name">Nabin Dangi</span>
          <span class="role">{{ currentRole }}</span>
        </h1>
        <p class="hero-description">
          Highly skilled, self-motivated electronics engineer passionate about learning
          new technologies and implementing them for the greater good. Specializing in
          firmware development and embedded systems.
        </p>
        <div class="hero-actions">
          <a href="#contact" @click="scrollToSection('contact')" class="btn btn-primary">
            Get In Touch
          </a>
          <a href="#projects" @click="scrollToSection('projects')" class="btn btn-outline">
            View My Work
          </a>
        </div>
        <div class="hero-links">
          <a href="https://github.com/Nabin-Flash320" target="_blank" class="social-link">
            <svg class="icon" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12 2C6.477 2 2 6.477 2 12c0 4.42 2.865 8.17 6.839 9.49.5.092.682-.217.682-.482 0-.237-.008-.866-.013-1.7-2.782.604-3.369-1.341-3.369-1.341-.454-1.155-1.11-1.462-1.11-1.462-.908-.62.069-.608.069-.608 1.003.07 1.531 1.03 1.531 1.03.892 1.529 2.341 1.087 2.91.831.092-.646.35-1.087.636-1.337-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.203 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.743 0 .267.18.578.688.48C19.138 20.167 22 16.418 22 12c0-5.523-4.477-10-10-10z"/>
            </svg>
          </a>
          <a href="https://www.linkedin.com/in/nabin-dangi-5879651aa/" target="_blank" class="social-link">
            <svg class="icon" fill="currentColor" viewBox="0 0 24 24">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
            </svg>
          </a>
          <a href="mailto:nabindangi32@gmail.com" class="social-link">
            <svg class="icon" fill="currentColor" viewBox="0 0 24 24">
              <path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-.904.732-1.636 1.636-1.636h.744L12 10.742l9.62-6.921h.744c.904 0 1.636.732 1.636 1.636z"/>
            </svg>
          </a>
        </div>
      </div>
              <div class="hero-visual">
        <div class="profile-container">
          <div class="profile-image">
            <img src="/src/assets/nabin-profile.jpg" alt="Nabin Dangi" />
            <div class="profile-ring"></div>
          </div>
          <!-- <div class="code-snippet">
            <div class="code-header">
              <div class="dots">
                <span class="dot red"></span>
                <span class="dot yellow"></span>
                <span class="dot green"></span>
              </div>
              <span class="filename">firmware.c</span>
            </div>
            <div class="code-content">
              <div class="code-line">
                <span class="keyword">#include</span>
                <span class="string">"esp_log.h"</span>
              </div>
              <div class="code-line">
                <span class="keyword">void</span>
                <span class="function">app_main</span>() {
              </div>
              <div class="code-line indent">
                <span class="function">ESP_LOGI</span>(<span class="string">"TAG"</span>,
                <span class="string">"Hello World!"</span>);
              </div>
              <div class="code-line">}</div>
            </div>
          </div> -->
        </div>
      </div>
    </div>
    <div class="hero-bg">
      <div class="circuit-pattern"></div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const roles = ['Firmware Developer', 'Electronics Engineer', 'Embedded Systems Expert']
const currentRole = ref(roles[0])
let roleIndex = 0
let intervalId: number | null = null

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

onMounted(() => {
  intervalId = setInterval(() => {
    roleIndex = (roleIndex + 1) % roles.length
    currentRole.value = roles[roleIndex]
  }, 3000) as number
})

onUnmounted(() => {
  if (intervalId) {
    clearInterval(intervalId)
  }
})
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  z-index: 2;
}

.greeting {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 1.2rem;
  color: #666;
  margin-bottom: 1rem;
}

.wave {
  animation: wave 2s infinite;
}

@keyframes wave {
  0%, 20%, 60%, 100% {
    transform: rotate(0deg);
  }
  10%, 30% {
    transform: rotate(-10deg);
  }
  40% {
    transform: rotate(10deg);
  }
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 1.5rem;
}

.name {
  display: block;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.role {
  display: block;
  color: #333;
  font-size: 2.5rem;
  margin-top: 0.5rem;
  opacity: 0;
  animation: fadeInUp 1s ease-out 0.5s forwards;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.hero-description {
  font-size: 1.2rem;
  color: #666;
  line-height: 1.7;
  margin-bottom: 2.5rem;
  max-width: 500px;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  margin-bottom: 2rem;
}

.hero-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 3rem;
  height: 3rem;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.9);
  color: #333;
  text-decoration: none;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.social-link:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

.icon {
  width: 1.5rem;
  height: 1.5rem;
}

.hero-visual {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.profile-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.profile-image {
  position: relative;
  width: 200px;
  height: 200px;
  border-radius: 50%;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  animation: profileFloat 6s ease-in-out infinite;
}

.profile-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

.profile-ring {
  position: absolute;
  top: -10px;
  left: -10px;
  right: -10px;
  bottom: -10px;
  border-radius: 50%;
  border: 3px solid transparent;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%) border-box;
  -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: exclude;
  mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
  animation: ringRotate 10s linear infinite;
}

@keyframes profileFloat {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

@keyframes ringRotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.code-snippet {
  background: #1e1e1e;
  border-radius: 1rem;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  transform: perspective(1000px) rotateY(-5deg) rotateX(5deg);
  animation: float 6s ease-in-out infinite;
}

@keyframes float {
  0%, 100% {
    transform: perspective(1000px) rotateY(-5deg) rotateX(5deg) translateY(0px);
  }
  50% {
    transform: perspective(1000px) rotateY(-5deg) rotateX(5deg) translateY(-10px);
  }
}

.code-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 1.5rem;
  background: #2d2d2d;
  border-bottom: 1px solid #3d3d3d;
}

.dots {
  display: flex;
  gap: 0.5rem;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.dot.red { background: #ff5f56; }
.dot.yellow { background: #ffbd2e; }
.dot.green { background: #27ca3f; }

.filename {
  color: #ccc;
  font-size: 0.9rem;
}

.code-content {
  padding: 1.5rem;
  font-family: 'Fira Code', monospace;
  font-size: 0.9rem;
  line-height: 1.6;
}

.code-line {
  margin-bottom: 0.5rem;
}

.indent {
  padding-left: 2rem;
}

.keyword { color: #569cd6; }
.function { color: #dcdcaa; }
.string { color: #ce9178; }

.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1;
}

.circuit-pattern {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image:
    radial-gradient(circle at 1px 1px, rgba(102, 126, 234, 0.15) 1px, transparent 0);
  background-size: 50px 50px;
  animation: move 20s linear infinite;
}

@keyframes move {
  0% {
    transform: translate(0, 0);
  }
  100% {
    transform: translate(50px, 50px);
  }
}

@media (max-width: 768px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }

  .hero-title {
    font-size: 2.5rem;
  }

  .role {
    font-size: 2rem;
  }

  .hero-actions {
    justify-content: center;
    flex-wrap: wrap;
  }

  .hero-links {
    justify-content: center;
  }

  .hero-visual {
    margin-top: 2rem;
  }

  .profile-image {
    width: 150px;
    height: 150px;
  }

  .code-snippet {
    transform: none;
    max-width: 100%;
  }
}
</style>
