<template>
  <section id="experience" class="section">
    <div class="container">
      <h2 class="section-title">Professional Experience</h2>
      <div class="timeline">
        <div
          v-for="(job, index) in experience"
          :key="index"
          class="timeline-item"
          :class="{ 'active': activeIndex === index }"
          @mouseenter="setActive(index)"
          @mouseleave="setActive(-1)"
        >
          <div class="timeline-marker">
            <div class="timeline-dot"></div>
          </div>
          <div class="timeline-content">
            <div class="job-header">
              <div class="job-info">
                <h3 class="job-title">{{ job.title }}</h3>
                <div class="company-link">
                  <a :href="job.companyUrl" target="_blank" class="company">
                    {{ job.company }}
                    <svg class="external-link" fill="currentColor" viewBox="0 0 20 20">
                      <path d="M11 3a1 1 0 100 2h2.586l-6.293 6.293a1 1 0 101.414 1.414L15 6.414V9a1 1 0 102 0V4a1 1 0 00-1-1h-5z"/>
                      <path d="M5 5a2 2 0 00-2 2v8a2 2 0 002 2h8a2 2 0 002-2v-1a1 1 0 10-2 0v1H5V7h1a1 1 0 000-2H5z"/>
                    </svg>
                  </a>
                </div>
              </div>
              <div class="job-meta">
                <span class="duration">{{ job.duration }}</span>
                <span class="location">{{ job.location }}</span>
              </div>
            </div>
            <ul class="achievements">
              <li v-for="(achievement, i) in job.achievements" :key="i">
                {{ achievement }}
              </li>
            </ul>
            <div class="technologies">
              <span
                v-for="tech in job.technologies"
                :key="tech"
                class="tech-tag"
              >
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface Experience {
  title: string
  company: string
  companyUrl: string
  duration: string
  location: string
  achievements: string[]
  technologies: string[]
}

const activeIndex = ref(-1)

const experience: Experience[] = [
  {
    title: 'Junior Firmware Developer',
    company: 'Ezlo Innovation Inc.',
    companyUrl: 'https://www.ezlopi.com/',
    duration: 'August 2022 - February 2025',
    location: 'Lalitpur, Nepal',
    achievements: [
      'Developed firmware for EzloPi, powered by the ESP32 chipset',
      'Implemented I2C, UART, SPI, ADC interfaces using ESP-IDF',
      'Created drivers for various sensors and technologies including mDNS and captive portal',
      'Gained deep understanding of embedded software development processes and architecture'
    ],
    technologies: ['ESP-IDF', 'C', 'ESP32', 'I2C', 'UART', 'SPI', 'ADC', 'mDNS']
  },
  {
    title: 'Firmware Developer Intern',
    company: 'Nepal Digital System',
    companyUrl: 'https://nepaldigisys.com/',
    duration: 'May 2022 - August 2022',
    location: 'Lalitpur, Nepal',
    achievements: [
      'Interfaced ESP32 devices using ESP-IDF framework',
      'Worked with wired communication protocols (UART, SPI, I2C)',
      'Implemented wireless protocols including BLE, BLE mesh, MQTT, and WiFi',
      'Gained hands-on experience with IoT device development'
    ],
    technologies: ['ESP-IDF', 'ESP32', 'BLE', 'BLE Mesh', 'MQTT', 'WiFi', 'UART', 'SPI', 'I2C']
  }
]

const setActive = (index: number) => {
  activeIndex.value = index
}
</script>

<style scoped>
.section {
  background: #fafafa;
}

.timeline {
  position: relative;
  max-width: 800px;
  margin: 0 auto;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 2rem;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(to bottom, #667eea, #764ba2);
}

.timeline-item {
  position: relative;
  margin-bottom: 3rem;
  padding-left: 5rem;
  transition: all 0.3s ease;
}

.timeline-item.active .timeline-content {
  transform: translateX(10px);
}

.timeline-marker {
  position: absolute;
  left: 0;
  top: 0;
}

.timeline-dot {
  width: 4rem;
  height: 4rem;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-weight: bold;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
  border: 4px solid white;
}

.timeline-content {
  background: white;
  border-radius: 1rem;
  padding: 2rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  border-left: 4px solid #667eea;
}

.timeline-item:hover .timeline-content {
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15);
}

.job-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 1.5rem;
  gap: 1rem;
}

.job-title {
  font-size: 1.3rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 0.5rem;
}

.company-link {
  display: flex;
  align-items: center;
}

.company {
  color: #667eea;
  text-decoration: none;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 0.25rem;
  transition: color 0.3s ease;
}

.company:hover {
  color: #764ba2;
}

.external-link {
  width: 1rem;
  height: 1rem;
}

.job-meta {
  text-align: right;
  flex-shrink: 0;
}

.duration {
  display: block;
  font-weight: 600;
  color: #333;
  margin-bottom: 0.25rem;
}

.location {
  display: block;
  color: #666;
  font-size: 0.9rem;
}

.achievements {
  list-style: none;
  margin: 0 0 1.5rem 0;
  padding: 0;
}

.achievements li {
  position: relative;
  padding-left: 1.5rem;
  margin-bottom: 0.75rem;
  color: #555;
  line-height: 1.6;
}

.achievements li::before {
  content: '▶';
  position: absolute;
  left: 0;
  color: #667eea;
  font-size: 0.8rem;
  top: 0.1rem;
}

.technologies {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-tag {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  padding: 0.25rem 0.75rem;
  border-radius: 1rem;
  font-size: 0.8rem;
  font-weight: 500;
}

@media (max-width: 768px) {
  .timeline::before {
    left: 1rem;
  }

  .timeline-item {
    padding-left: 3rem;
  }

  .timeline-dot {
    width: 2rem;
    height: 2rem;
    left: 0;
  }

  .job-header {
    flex-direction: column;
    align-items: flex-start;
  }

  .job-meta {
    text-align: left;
  }

  .achievements li {
    font-size: 0.9rem;
  }
}
</style>
