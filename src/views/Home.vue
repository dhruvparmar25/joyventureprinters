<template>
  <div class="home">
    <!-- Hero Section -->
    <section class="hero">
      <div class="container">
        <div class="hero-content">
          <h1>Professional Printing Solutions</h1>
          <p>Quality prints that make your business stand out</p>
          <router-link to="/contact" class="btn btn-primary">Get a Quote</router-link>
        </div>
      </div>
    </section>

    <!-- Services Overview -->
    <section class="services-overview section">
      <div class="container">
        <div class="section-title">
          <h2>Our Services</h2>
          <p>Comprehensive printing solutions for all your needs</p>
        </div>
        <div class="services-grid">
          <div class="service-card" v-for="service in services" :key="service.id">
            <div class="service-icon">
              <i :class="service.icon"></i>
            </div>
            <h3>{{ service.title }}</h3>
            <p>{{ service.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Why Choose Us -->
    <section class="why-choose-us section">
      <div class="container">
        <div class="section-title">
          <h2>Why Choose Us</h2>
          <p>Experience the difference with our professional printing services</p>
        </div>
        <div class="features-grid">
          <div class="feature" v-for="feature in features" :key="feature.id">
            <div class="feature-icon">
              <i :class="feature.icon"></i>
            </div>
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section">
      <div class="container">
        <div class="cta-content">
          <h2>Ready to Start Your Project?</h2>
          <p>Get in touch with us today for a free consultation</p>
          <router-link to="/contact" class="btn btn-secondary">Contact Us</router-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const services = ref([
  {
    id: 1,
    title: 'Digital Printing',
    description: 'High-quality digital prints for small to medium runs',
    icon: 'fas fa-print'
  },
  {
    id: 2,
    title: 'Offset Printing',
    description: 'Cost-effective solutions for large print runs',
    icon: 'fas fa-copy'
  },
  {
    id: 3,
    title: 'Custom Printing',
    description: 'Personalized printing solutions for unique projects',
    icon: 'fas fa-paint-brush'
  }
])

const features = ref([
  {
    id: 1,
    title: 'Quality Guaranteed',
    description: 'We ensure the highest quality in every print job',
    icon: 'fas fa-check-circle'
  },
  {
    id: 2,
    title: 'Fast Turnaround',
    description: 'Quick delivery without compromising quality',
    icon: 'fas fa-clock'
  },
  {
    id: 3,
    title: 'Expert Support',
    description: 'Professional guidance throughout your project',
    icon: 'fas fa-headset'
  }
])
</script>

<style lang="scss" scoped>
.home {
  padding-top: 80px; // Account for fixed navbar
}

.hero {
  background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1588666309990-d68f08e3d4a6?w=1920&q=80');
  background-size: cover;
  background-position: center;
  height: 80vh;
  display: flex;
  align-items: center;
  color: var(--white);
  text-align: center;

  .hero-content {
    max-width: 800px;
    margin: 0 auto;
    padding: 0 20px;

    h1 {
      font-size: 3.5rem;
      margin-bottom: 1rem;
    }

    p {
      font-size: 1.2rem;
      margin-bottom: 2rem;
    }
  }
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.service-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  text-align: center;
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-5px);
  }

  .service-icon {
    font-size: 2.5rem;
    color: var(--primary-color);
    margin-bottom: 1rem;
  }

  h3 {
    margin-bottom: 1rem;
    color: var(--primary-color);
  }
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.feature {
  text-align: center;
  padding: 2rem;
  background: var(--light-bg);
  border-radius: 8px;

  .feature-icon {
    font-size: 2rem;
    color: var(--secondary-color);
    margin-bottom: 1rem;
  }

  h3 {
    margin-bottom: 1rem;
    color: var(--primary-color);
  }
}

.cta-section {
  background: var(--primary-color);
  color: var(--white);
  padding: 4rem 0;
  text-align: center;

  .cta-content {
    max-width: 600px;
    margin: 0 auto;

    h2 {
      font-size: 2.5rem;
      margin-bottom: 1rem;
    }

    p {
      margin-bottom: 2rem;
    }
  }
}

@media (max-width: 768px) {
  .hero {
    height: 60vh;

    .hero-content h1 {
      font-size: 2.5rem;
    }
  }
}
</style> 