<template>
  <section id="about" class="section">
    <div class="container">
      <div class="about-content">
        <div class="about-text">
          <h2 class="section-title">About Me</h2>
          <div class="intro">
            <p class="lead">
              Hi, I'm <strong>Nabin Dangi</strong>, a highly skilled and self-motivated
              electronics engineer passionate about learning new technologies and
              implementing them for the greater good.
            </p>
            <p>
              With over <strong>2.5+ years</strong> of professional experience in firmware
              development, I specialize in creating robust embedded solutions using ESP32
              and other microcontroller platforms. My journey in electronics engineering
              has led me to work on diverse projects ranging from IoT devices to
              sophisticated embedded systems.
            </p>
            <p>
              I'm particularly passionate about <strong>embedded systems</strong>,
              <strong>firmware development</strong>, and <strong>IoT solutions</strong>.
              My expertise spans across multiple programming languages and technologies,
              with a strong focus on C/C++ for embedded systems and Python for backend
              development and data analysis.
            </p>
          </div>

          <div class="highlights">
            <h3>What I Bring</h3>
            <div class="highlight-grid">
              <div class="highlight-item">
                <div class="highlight-icon">🚀</div>
                <div class="highlight-content">
                  <h4>Innovation</h4>
                  <p>Constantly exploring cutting-edge technologies and implementing creative solutions</p>
                </div>
              </div>
              <div class="highlight-item">
                <div class="highlight-icon">⚡</div>
                <div class="highlight-content">
                  <h4>Performance</h4>
                  <p>Optimized firmware development with focus on efficiency and reliability</p>
                </div>
              </div>
              <div class="highlight-item">
                <div class="highlight-icon">🤝</div>
                <div class="highlight-content">
                  <h4>Collaboration</h4>
                  <p>Strong team player with excellent communication and project management skills</p>
                </div>
              </div>
              <div class="highlight-item">
                <div class="highlight-icon">📚</div>
                <div class="highlight-content">
                  <h4>Learning</h4>
                  <p>Continuous learner staying updated with latest industry trends and technologies</p>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="about-stats">
          <div class="stats-card">
            <h3>Quick Stats</h3>
            <div class="stats-grid">
              <div class="stat-item">
                <div class="stat-number">2.5+</div>
                <div class="stat-label">Years Experience</div>
              </div>
              <div class="stat-item">
                <div class="stat-number">8+</div>
                <div class="stat-label">Projects Completed</div>
              </div>
              <div class="stat-item">
                <div class="stat-number">10+</div>
                <div class="stat-label">Technologies</div>
              </div>
              <div class="stat-item">
                <div class="stat-number">2</div>
                <div class="stat-label">Awards Won</div>
              </div>
            </div>
          </div>

          <div class="education-card">
            <h3>Education</h3>
            <div class="education-item">
              <div class="education-icon">🎓</div>
              <div class="education-info">
                <h4>Bachelor of Engineering</h4>
                <p class="institution">Kantipur Engineering College</p>
                <p class="duration">2017 - 2023</p>
                <p class="location">Lalitpur, Nepal</p>
              </div>
            </div>
            <div class="education-item">
              <div class="education-icon">📖</div>
              <div class="education-info">
                <h4>Higher Secondary Studies</h4>
                <p class="institution">Eagerbridge Higher Secondary School</p>
                <p class="duration">2015 - 2017</p>
                <p class="location">Surkhet, Nepal</p>
              </div>
            </div>
          </div>

          <div class="interests-card">
            <h3>Interests</h3>
            <div class="interests-grid">
              <div class="interest-item">
                <span class="interest-icon">💻</span>
                <span>Technology</span>
              </div>
              <div class="interest-item">
                <span class="interest-icon">🎵</span>
                <span>Music</span>
              </div>
              <div class="interest-item">
                <span class="interest-icon">🎬</span>
                <span>Movies</span>
              </div>
              <div class="interest-item">
                <span class="interest-icon">🌍</span>
                <span>Innovation</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// No reactive data needed for this component
</script>

<style scoped>
.section {
  background: white;
}

.about-content {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 4rem;
  align-items: start;
}

.about-text {
  max-width: none;
}

.section-title {
  text-align: left;
  margin-bottom: 2rem;
}

.intro p {
  font-size: 1.1rem;
  line-height: 1.7;
  color: #555;
  margin-bottom: 1.5rem;
}

.lead {
  font-size: 1.3rem !important;
  color: #333 !important;
  font-weight: 500;
}

.highlights {
  margin-top: 3rem;
}

.highlights h3 {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1.5rem;
}

.highlight-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

.highlight-item {
  display: flex;
  gap: 1rem;
  padding: 1rem;
  background: #f8f9fa;
  border-radius: 1rem;
  transition: transform 0.3s ease;
}

.highlight-item:hover {
  transform: translateY(-3px);
  background: rgba(102, 126, 234, 0.05);
}

.highlight-icon {
  font-size: 1.5rem;
  width: 3rem;
  height: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 0.75rem;
  flex-shrink: 0;
}

.highlight-content h4 {
  font-size: 1rem;
  font-weight: 700;
  color: #333;
  margin: 0 0 0.25rem 0;
}

.highlight-content p {
  font-size: 0.9rem;
  color: #666;
  margin: 0;
  line-height: 1.4;
}

.about-stats {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.stats-card,
.education-card,
.interests-card {
  background: white;
  border-radius: 1.5rem;
  padding: 2rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  border: 1px solid #f0f0f0;
}

.stats-card h3,
.education-card h3,
.interests-card h3 {
  font-size: 1.25rem;
  font-weight: 700;
  color: #1a1a1a;
  margin: 0 0 1.5rem 0;
  text-align: center;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
}

.stat-item {
  text-align: center;
  padding: 1rem;
  background: #f8f9fa;
  border-radius: 0.75rem;
}

.stat-number {
  font-size: 2rem;
  font-weight: 800;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  display: block;
}

.stat-label {
  font-size: 0.9rem;
  color: #666;
  font-weight: 600;
  margin-top: 0.25rem;
}

.education-item {
  display: flex;
  gap: 1rem;
  padding: 1rem 0;
  border-bottom: 1px solid #f0f0f0;
}

.education-item:last-child {
  border-bottom: none;
  padding-bottom: 0;
}

.education-icon {
  font-size: 1.5rem;
  width: 3rem;
  height: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 0.75rem;
  flex-shrink: 0;
}

.education-info h4 {
  font-size: 1rem;
  font-weight: 700;
  color: #333;
  margin: 0 0 0.25rem 0;
}

.institution {
  color: #667eea;
  font-weight: 600;
  margin: 0 0 0.25rem 0;
  font-size: 0.9rem;
}

.duration,
.location {
  color: #666;
  font-size: 0.85rem;
  margin: 0;
}

.interests-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
}

.interest-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem;
  background: #f8f9fa;
  border-radius: 0.75rem;
  font-weight: 600;
  color: #333;
  transition: background 0.3s ease;
}

.interest-item:hover {
  background: rgba(102, 126, 234, 0.1);
}

.interest-icon {
  font-size: 1.25rem;
}

@media (max-width: 1024px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .section-title {
    text-align: center;
  }

  .highlight-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 768px) {
  .about-content {
    gap: 2rem;
  }

  .intro p {
    font-size: 1rem;
  }

  .lead {
    font-size: 1.1rem !important;
  }

  .stats-card,
  .education-card,
  .interests-card {
    padding: 1.5rem;
  }

  .stats-grid {
    grid-template-columns: 1fr;
    gap: 0.75rem;
  }

  .interests-grid {
    grid-template-columns: 1fr;
  }

  .highlight-item {
    flex-direction: column;
    text-align: center;
  }

  .highlight-content {
    text-align: center;
  }
}
</style>
