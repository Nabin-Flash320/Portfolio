<template>
  <section id="skills" class="section">
    <div class="container">
      <h2 class="section-title">Skills & Technologies</h2>
      <div class="skills-container">
        <div
          v-for="(category, index) in skillCategories"
          :key="index"
          class="skill-category"
        >
          <div class="category-header">
            <div class="category-icon">
              <component :is="category.icon" class="icon" />
            </div>
            <h3 class="category-title">{{ category.name }}</h3>
          </div>
          <div class="skills-grid">
            <div
              v-for="skill in category.skills"
              :key="skill.name"
              class="skill-item"
              :class="{ 'expert': skill.level === 'expert', 'advanced': skill.level === 'advanced' }"
            >
              <div class="skill-icon">
                <img
                  v-if="skill.icon.startsWith('http')"
                  :src="skill.icon"
                  :alt="skill.name + ' logo'"
                  loading="lazy"
                  @error="handleImageError"
                />
                <span v-else>{{ skill.icon }}</span>
              </div>
              <div class="skill-info">
                <span class="skill-name">{{ skill.name }}</span>
                <div class="skill-level">
                  <div
                    class="level-bar"
                    :style="{ width: getLevelWidth(skill.level) }"
                  ></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="certifications">
        <h3 class="certifications-title">Certifications & Awards</h3>
        <div class="certifications-grid">
          <div
            v-for="cert in certifications"
            :key="cert.title"
            class="certification-card"
          >
            <div class="cert-icon">🏆</div>
            <div class="cert-info">
              <h4 class="cert-title">{{ cert.title }}</h4>
              <p class="cert-issuer">{{ cert.issuer }}</p>
              <span class="cert-date">{{ cert.date }}</span>
              <a v-if="cert.link" :href="cert.link" target="_blank" class="cert-link">
                View Certificate →
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { defineComponent, h } from 'vue'

interface Skill {
  name: string
  icon: string
  level: 'beginner' | 'intermediate' | 'advanced' | 'expert'
}

interface SkillCategory {
  name: string
  icon: any
  skills: Skill[]
}

interface Certification {
  title: string
  issuer: string
  date: string
  link?: string
}

// Custom icons as Vue components
const CodeIcon = defineComponent({
  render: () => h('svg', {
    fill: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      d: 'M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4'
    })
  ])
})

const ChipIcon = defineComponent({
  render: () => h('svg', {
    fill: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      d: 'M8 9l3 3-3 3m5 0h3M5 20h14a2 2 0 002-2V6a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z'
    })
  ])
})

const WebIcon = defineComponent({
  render: () => h('svg', {
    fill: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      d: 'M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.94-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z'
    })
  ])
})

const DataIcon = defineComponent({
  render: () => h('svg', {
    fill: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      d: 'M9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4zm2.5 2.5h-15V5h15v14.5zm0-16.5h-15c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h15c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2z'
    })
  ])
})

const ToolsIcon = defineComponent({
  render: () => h('svg', {
    fill: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      d: 'M22.7 19l-9.1-9.1c.9-2.3.4-5-1.5-6.9-2-2-5-2.4-7.4-1.3L9 6 6 9 1.6 4.7C.4 7.1.9 10.1 2.9 12.1c1.9 1.9 4.6 2.4 6.9 1.5l9.1 9.1c.4.4 1 .4 1.4 0l2.3-2.3c.5-.4.5-1.1.1-1.4z'
    })
  ])
})

const skillCategories: SkillCategory[] = [
  {
    name: 'Programming Languages',
    icon: CodeIcon,
    skills: [
      { name: 'C', icon: 'https://upload.wikimedia.org/wikipedia/commons/1/19/C_Logo.png', level: 'expert' },
      { name: 'C++', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/cplusplus/cplusplus-original.svg', level: 'advanced' },
      { name: 'Python', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg', level: 'advanced' },
      { name: 'Go', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg', level: 'intermediate' },
      { name: 'PHP', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg', level: 'intermediate' }
    ]
  },
  {
    name: 'Embedded & IoT',
    icon: ChipIcon,
    skills: [
      { name: 'ESP32', icon: 'https://m1cr0lab-esp32.github.io/remote-control-with-websocket/logo/thumbnail.png', level: 'expert' },
      { name: 'Arduino', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/arduino/arduino-original.svg', level: 'expert' },
      { name: 'ESP-IDF', icon: 'https://cdn.worldvectorlogo.com/logos/espressif-systems.svg', level: 'expert' },
      { name: 'LVGL', icon: 'https://lvgl.io/', level: 'intermediate' },
      { name: 'BLE/BLE Mesh', icon: 'https://cdn.worldvectorlogo.com/logos/bluetooth-3.svg', level: 'advanced' },
      { name: 'WiFi', icon: 'https://cdn.worldvectorlogo.com/logos/wifi-2.svg', level: 'advanced' },
      { name: 'MQTT', icon: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTrIgzxbVSPZ4Ycxr0OmdBhUWaqp5_ieVFwDQ&s', level: 'advanced' },
      { name: 'I2C/SPI/UART', icon: 'https://e7.pngegg.com/pngimages/773/477/png-clipart-serial-port-computer-icons-computer-port-usb-port-universal-serial-bus-usb-icon-miscellaneous-angle-thumbnail.png', level: 'expert' },
      { name: 'Modbus', icon: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTYnGZZMs_RUxs2KYD6fiQm5pmNukaKTncaww&s', level: 'advanced' },
    ]
  },
  {
    name: 'Web Technologies',
    icon: WebIcon,
    skills: [
      { name: 'Django', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/django/django-plain.svg', level: 'advanced' },
      { name: 'Flask', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flask/flask-original.svg', level: 'intermediate' },
      { name: 'Laravel', icon: 'https://cdn.worldvectorlogo.com/logos/laravel-3.svg', level: 'intermediate' },
      { name: 'Gin', icon: 'https://gin-gonic.com/_astro/gin.D6H2T_2v_ZD2G7l.webp', level: 'intermediate' },
      { name: 'Vue.js', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg', level: 'intermediate' }
    ]
  },
  {
    name: 'Data Science & ML',
    icon: DataIcon,
    skills: [
      { name: 'Pandas', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/pandas/pandas-original.svg', level: 'advanced' },
      { name: 'PyTorch', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/pytorch/pytorch-original.svg', level: 'intermediate' },
      { name: 'OpenCV', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/opencv/opencv-original.svg', level: 'intermediate' }
    ]
  },
  {
    name: 'Tools & Technologies',
    icon: ToolsIcon,
    skills: [
      { name: 'Git/GitHub', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg', level: 'advanced' },
      { name: 'Qt', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/qt/qt-original.svg', level: 'intermediate' },
      { name: 'Raspberry Pi', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/raspberrypi/raspberrypi-original.svg', level: 'intermediate' }
    ]
  }
]

const certifications: Certification[] = [
  {
    title: 'Deep Learning with PyTorch: Zero to GANs',
    issuer: 'Jovian',
    date: 'July 2020',
    link: 'https://jovian.com/certificate/MFQWCMRRGU'
  },
  {
    title: 'Data Analysis with Python: Zero to Pandas',
    issuer: 'Jovian',
    date: 'July 2020',
    link: 'https://jovian.com/certificate/MFQWCOJZHA'
  },
  {
    title: '1st Place - Sagarmatha Tech Fest',
    issuer: 'Health Monitoring Band Project',
    date: '2022'
  },
  {
    title: 'KEC Conference Publication',
    issuer: 'Health Monitoring Band Featured',
    date: '2022'
  }
]

const getLevelWidth = (level: string): string => {
  const levels = {
    beginner: '25%',
    intermediate: '50%',
    advanced: '75%',
    expert: '100%'
  }
  return levels[level as keyof typeof levels] || '0%'
}

const handleImageError = (event: Event) => {
  const img = event.target as HTMLImageElement
  img.style.display = 'none'
  const parent = img.parentElement
  if (parent) {
    parent.innerHTML = '🔧' // Fallback icon
    parent.style.fontSize = '1.5rem'
  }
}
</script>

<style scoped>
.section {
  background: #fafafa;
}

.skills-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  margin-bottom: 4rem;
}

.skill-category {
  background: white;
  border-radius: 1.5rem;
  padding: 2rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.skill-category:hover {
  transform: translateY(-5px);
}

.category-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.category-icon {
  width: 3rem;
  height: 3rem;
  border-radius: 1rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}

.icon {
  width: 1.5rem;
  height: 1.5rem;
}

.category-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: #1a1a1a;
  margin: 0;
}

.skills-grid {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.skill-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 0.75rem;
  border-radius: 0.75rem;
  background: #f8f9fa;
  transition: all 0.3s ease;
}

.skill-item:hover {
  background: #e9ecef;
  transform: translateX(5px);
}

.skill-item.expert {
  background: rgba(102, 126, 234, 0.1);
  border: 1px solid rgba(102, 126, 234, 0.2);
}

.skill-item.advanced {
  background: rgba(118, 75, 162, 0.1);
  border: 1px solid rgba(118, 75, 162, 0.2);
}

.skill-icon {
  width: 2.5rem;
  height: 2.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  flex-shrink: 0;
}

.skill-icon img {
  width: 1.8rem;
  height: 1.8rem;
  object-fit: contain;
}

.skill-icon:not(:has(img)) {
  font-size: 1.5rem;
}

.skill-info {
  flex: 1;
}

.skill-name {
  font-weight: 600;
  color: #333;
  display: block;
  margin-bottom: 0.25rem;
}

.skill-level {
  width: 100%;
  height: 4px;
  background: #e9ecef;
  border-radius: 2px;
  overflow: hidden;
}

.level-bar {
  height: 100%;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 2px;
  transition: width 1s ease-out;
}

.certifications {
  background: white;
  border-radius: 1.5rem;
  padding: 2rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

.certifications-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1.5rem;
  text-align: center;
}

.certifications-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}

.certification-card {
  display: flex;
  gap: 1rem;
  padding: 1.5rem;
  background: linear-gradient(135deg, #fff9e6 0%, #ffeaa7 20%);
  border-radius: 1rem;
  border: 1px solid #fdcb6e;
  transition: transform 0.3s ease;
}

.certification-card:hover {
  transform: translateY(-3px);
}

.cert-icon {
  font-size: 2rem;
  flex-shrink: 0;
}

.cert-info {
  flex: 1;
}

.cert-title {
  font-size: 1rem;
  font-weight: 700;
  color: #333;
  margin: 0 0 0.25rem 0;
  line-height: 1.3;
}

.cert-issuer {
  color: #666;
  font-size: 0.9rem;
  margin: 0 0 0.25rem 0;
}

.cert-date {
  color: #888;
  font-size: 0.8rem;
  display: block;
  margin-bottom: 0.5rem;
}

.cert-link {
  color: #667eea;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.9rem;
  transition: color 0.3s ease;
}

.cert-link:hover {
  color: #764ba2;
}

@media (max-width: 768px) {
  .skills-container {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .skill-category {
    padding: 1.5rem;
  }

  .category-header {
    gap: 0.75rem;
  }

  .category-icon {
    width: 2.5rem;
    height: 2.5rem;
  }

  .icon {
    width: 1.25rem;
    height: 1.25rem;
  }

  .certifications-grid {
    grid-template-columns: 1fr;
  }

  .certification-card {
    padding: 1rem;
  }
}
</style>
