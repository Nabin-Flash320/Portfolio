<template>
  <section id="projects" class="section">
    <div class="container">
      <h2 class="section-title">Featured Projects</h2>
      <div class="projects-grid">
        <div
          v-for="(project, index) in projects"
          :key="index"
          class="project-card"
          :class="{ 'featured': project.featured }"
        >
          <div class="project-header">
            <div class="project-icon">
              <svg v-if="project.type === 'firmware'" fill="currentColor" viewBox="0 0 24 24">
                <path d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
              </svg>
              <svg v-else-if="project.type === 'iot'" fill="currentColor" viewBox="0 0 24 24">
                <path d="M8 9l3 3-3 3m5 0h3M5 20h14a2 2 0 002-2V6a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/>
              </svg>
              <svg v-else fill="currentColor" viewBox="0 0 24 24">
                <path d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"/>
              </svg>
            </div>
            <div class="project-links">
              <a v-if="project.github" :href="project.github" target="_blank" class="project-link">
                <svg fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 2C6.477 2 2 6.477 2 12c0 4.42 2.865 8.17 6.839 9.49.5.092.682-.217.682-.482 0-.237-.008-.866-.013-1.7-2.782.604-3.369-1.341-3.369-1.341-.454-1.155-1.11-1.462-1.11-1.462-.908-.62.069-.608.069-.608 1.003.07 1.531 1.03 1.531 1.03.892 1.529 2.341 1.087 2.91.831.092-.646.35-1.087.636-1.337-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.203 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.743 0 .267.18.578.688.48C19.138 20.167 22 16.418 22 12c0-5.523-4.477-10-10-10z"/>
                </svg>
              </a>
              <a v-if="project.demo" :href="project.demo" target="_blank" class="project-link">
                <svg fill="currentColor" viewBox="0 0 24 24">
                  <path d="M10 6V4a2 2 0 00-2-2H4a2 2 0 00-2 2v2a2 2 0 002 2h4a2 2 0 002-2zm10 0V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2a2 2 0 002 2h4a2 2 0 002-2zM10 18v-2a2 2 0 00-2-2H4a2 2 0 00-2 2v2a2 2 0 002 2h4a2 2 0 002-2zm10 0v-2a2 2 0 00-2-2h-4a2 2 0 00-2 2v2a2 2 0 002 2h4a2 2 0 002-2z"/>
                </svg>
              </a>
            </div>
          </div>

          <h3 class="project-title">{{ project.title }}</h3>
          <p class="project-description">{{ project.description }}</p>

          <ul class="project-features">
            <li v-for="feature in project.features" :key="feature">
              {{ feature }}
            </li>
          </ul>

          <div class="project-technologies">
            <span
              v-for="tech in project.technologies"
              :key="tech"
              class="tech-badge"
            >
              {{ tech }}
            </span>
          </div>

          <div v-if="project.awards" class="project-awards">
            <div class="award" v-for="award in project.awards" :key="award">
              🏆 {{ award }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
interface Project {
  title: string
  description: string
  features: string[]
  technologies: string[]
  type: 'firmware' | 'iot' | 'software'
  github?: string
  demo?: string
  featured?: boolean
  awards?: string[]
}

const projects: Project[] = [
  {
    title: 'EzloPi',
    description: 'Collaborative open-source firmware project for ESP32-based IoT devices, enabling seamless smart home automation.',
    features: [
      'ESP32 firmware development using ESP-IDF',
      'ADC and UART implementation for sensor integration',
      'Driver development for DHT22, DS18B20, dimmable lamps',
      'API integration with captive portal and mDNS'
    ],
    technologies: ['ESP-IDF', 'C', 'ESP32', 'IoT', 'APIs'],
    type: 'firmware',
    github: 'https://github.com/ezloteam/Ezlo_Pi',
    featured: true
  },
  {
    title: 'Smart Shopping Cart',
    description: 'Automated shopping cart system with RFID detection, image processing, and seamless checkout experience.',
    features: [
      'Automatic human detection using RFID and image processing',
      'Real-time item scanning and registration system',
      'Automatic checkout with QR code payment integration',
      'Shopping cart UI with OpenCV image detection'
    ],
    technologies: ['Arduino', 'Python', 'Django', 'PyQt', 'RaspberryPi', 'OpenCV', 'RFID'],
    type: 'iot',
    github: 'https://github.com/Nabin-Flash320/Cart-UI',
    featured: true
  },
  {
    title: 'Health Monitoring Band',
    description: 'Wearable device for continuous health monitoring with Bluetooth connectivity and emergency notifications.',
    features: [
      'Real-time pulse rate and temperature monitoring',
      'Bluetooth connectivity for mobile phone syncing',
      'Emergency notification system to registered contacts',
      'Wearable wristwatch form factor'
    ],
    technologies: ['Arduino', 'Bluetooth', 'Sensors', 'Mobile Integration'],
    type: 'iot',
    awards: ['1st Place - Sagarmatha Tech Fest', 'Featured in KEC Conference Publication']
  },
  {
    title: 'Earth-O-Help',
    description: 'Disaster response robotic system with autonomous navigation and human detection capabilities.',
    features: [
      'Dual robot system for disaster area navigation',
      'Human detection using sound and ultrasonic sensors',
      'Live video footage transmission for rescue operations',
      'Autonomous navigation in challenging environments'
    ],
    technologies: ['RaspberryPi', 'Arduino', 'PyTorch', 'WebSocket', 'Computer Vision'],
    type: 'iot'
  },
  {
    title: 'ESP OTA using GitHub',
    description: 'Over-the-air firmware update system leveraging GitHub releases for ESP32 devices.',
    features: [
      'OTA updates using GitHub release binaries',
      'Support for private repository access',
      'Secure firmware distribution mechanism',
      'Version management and rollback capabilities'
    ],
    technologies: ['ESP-IDF', 'C', 'GitHub API', 'OTA'],
    type: 'firmware',
    github: 'https://github.com/Nabin-Flash320/esp-ota-using-github'
  },
  {
    title: 'LCD Interface with LVGL',
    description: 'Advanced display interface implementation using LVGL graphics library for ESP32.',
    features: [
      'ILI9486 display (380x480) interfacing',
      '8-bit I80 interface implementation',
      'LVGL graphics library integration',
      'Responsive UI components'
    ],
    technologies: ['ESP-IDF', 'LVGL', 'C', 'Graphics'],
    type: 'firmware',
    github: 'https://github.com/Nabin-Flash320/LCD_Project'
  },
  {
    title: 'BLE Wrapper Library',
    description: 'Simplified BLE implementation wrapper for ESP-IDF, streamlining GATT server and client development.',
    features: [
      'Simplified GATT attribute implementation',
      'Easy server and client connection management',
      'Streamlined BLE development workflow',
      'Comprehensive documentation and examples'
    ],
    technologies: ['ESP-IDF', 'C', 'BLE', 'GATT'],
    type: 'firmware',
    github: 'https://github.com/Nabin-Flash320/ESP-BLE'
  },
  {
    title: 'Sorting Algorithm Visualizer',
    description: 'Interactive visualization of sorting algorithms using C++ graphics library.',
    features: [
      'Visual representation of bubble, insertion, selection sorts',
      'Quick sort algorithm visualization',
      'Real-time sorting process animation',
      'Educational tool for algorithm learning'
    ],
    technologies: ['C++', 'Graphics.h', 'Algorithms'],
    type: 'software',
    github: 'https://github.com/Nabin-Flash320/c-Graphics'
  }
]
</script>

<style scoped>
.section {
  background: white;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  gap: 2rem;
  max-width: 1400px;
  margin: 0 auto;
}

.project-card {
  background: white;
  border-radius: 1.5rem;
  padding: 2rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  border: 1px solid #f0f0f0;
  position: relative;
  overflow: hidden;
}

.project-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  transform: scaleX(0);
  transition: transform 0.3s ease;
}

.project-card:hover::before {
  transform: scaleX(1);
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
}

.project-card.featured {
  border: 2px solid #667eea;
  position: relative;
}

.project-card.featured::after {
  content: '⭐ Featured';
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 0.25rem 0.75rem;
  border-radius: 1rem;
  font-size: 0.8rem;
  font-weight: 600;
}

.project-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.project-icon {
  width: 3rem;
  height: 3rem;
  border-radius: 0.75rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}

.project-icon svg {
  width: 1.5rem;
  height: 1.5rem;
}

.project-links {
  display: flex;
  gap: 0.5rem;
}

.project-link {
  width: 2.5rem;
  height: 2.5rem;
  border-radius: 0.5rem;
  background: #f8f9fa;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #666;
  text-decoration: none;
  transition: all 0.3s ease;
}

.project-link:hover {
  background: #667eea;
  color: white;
  transform: scale(1.1);
}

.project-link svg {
  width: 1.25rem;
  height: 1.25rem;
}

.project-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1rem;
}

.project-description {
  color: #666;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.project-features {
  list-style: none;
  margin: 0 0 1.5rem 0;
  padding: 0;
}

.project-features li {
  position: relative;
  padding-left: 1.5rem;
  margin-bottom: 0.5rem;
  color: #555;
  font-size: 0.9rem;
  line-height: 1.5;
}

.project-features li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: #667eea;
  font-weight: bold;
}

.project-technologies {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.tech-badge {
  background: rgba(102, 126, 234, 0.1);
  color: #667eea;
  padding: 0.25rem 0.75rem;
  border-radius: 1rem;
  font-size: 0.8rem;
  font-weight: 500;
  border: 1px solid rgba(102, 126, 234, 0.2);
}

.project-awards {
  background: linear-gradient(135deg, #fff9e6 0%, #ffeaa7 100%);
  border-radius: 0.75rem;
  padding: 1rem;
  border: 1px solid #fdcb6e;
}

.award {
  font-size: 0.9rem;
  font-weight: 600;
  color: #e17055;
  margin-bottom: 0.25rem;
}

.award:last-child {
  margin-bottom: 0;
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .project-card {
    padding: 1.5rem;
  }

  .project-header {
    margin-bottom: 1rem;
  }

  .project-icon {
    width: 2.5rem;
    height: 2.5rem;
  }

  .project-icon svg {
    width: 1.25rem;
    height: 1.25rem;
  }

  .project-title {
    font-size: 1.25rem;
  }
}
</style>
