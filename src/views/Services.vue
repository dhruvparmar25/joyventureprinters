<template>
  <div class="services">
    <!-- Services Hero -->
    <section class="services-hero">
      <div class="container">
        <h1>Our Services</h1>
        <p>Comprehensive printing solutions for all your needs</p>
      </div>
    </section>

    <!-- Main Services -->
    <section class="main-services section">
      <div class="container">
        <div class="section-title">
          <h2>Printing Solutions</h2>
          <p>Discover our range of professional printing services</p>
        </div>
        <div class="services-grid">
          <div v-for="service in mainServices" :key="service.id" class="service-item">
            <div class="service-image">
              <img :src="service.image" :alt="service.title">
            </div>
            <div class="service-content">
              <h3>{{ service.title }}</h3>
              <p>{{ service.description }}</p>
              <ul class="service-features">
                <li v-for="(feature, index) in service.features" :key="index">
                  <i class="fas fa-check"></i> {{ feature }}
                </li>
              </ul>
              <router-link :to="service.ctaLink" class="btn btn-primary">
                Learn More
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Pricing Section -->
    <section class="pricing section">
      <div class="container">
        <div class="section-title">
          <h2>Pricing Packages</h2>
          <p>Choose the perfect package for your needs</p>
        </div>
        <div class="pricing-grid">
          <div v-for="pkg in pricingPackages" :key="pkg.id" class="pricing-card">
            <div class="package-header">
              <h3>{{ pkg.name }}</h3>
              <div class="price">
                <span class="currency">₹</span>
                <span class="amount">{{ pkg.price }}</span>
                <span class="period">/{{ pkg.period }}</span>
              </div>
            </div>
            <ul class="package-features">
              <li v-for="(feature, index) in pkg.features" :key="index">
                <i class="fas fa-check"></i> {{ feature }}
              </li>
            </ul>
            <router-link to="/contact" class="btn btn-secondary">
              Get Started
            </router-link>
          </div>
        </div>
      </div>
    </section>

    <!-- Additional Services -->
    <section class="additional-services section">
      <div class="container">
        <div class="section-title">
          <h2>Additional Services</h2>
          <p>Extra services to enhance your printing experience</p>
        </div>
        <div class="additional-services-grid">
          <div v-for="service in additionalServices" :key="service.id" class="additional-service">
            <div class="service-icon">
              <i :class="service.icon"></i>
            </div>
            <h3>{{ service.title }}</h3>
            <p>{{ service.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section">
      <div class="container">
        <div class="cta-content">
          <h2>Need a Custom Solution?</h2>
          <p>Contact us for a personalized quote tailored to your specific needs</p>
          <router-link to="/contact" class="btn btn-primary">Get a Quote</router-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const mainServices = ref([
  {
    id: 1,
    title: "Digital Printing",
    description: "High-quality digital prints for small to medium runs with quick turnaround times.",
    image: "https://images.unsplash.com/photo-1562654501-a0ccc0fc3fb1?w=800&q=80",
    features: [
      "Full-color printing",
      "Variable data printing",
      "Quick turnaround",
      "Cost-effective for small runs"
    ],
    ctaLink: "/services/digital-printing"
  },
  {
    id: 2,
    title: "Offset Printing",
    description: "Professional offset printing for large volume projects with superior quality.",
    image: "https://images.unsplash.com/photo-1562654435-c3c7164caa4f?w=800&q=80",
    features: [
      "High-quality results",
      "Cost-effective for large runs",
      "Wide range of paper options",
      "Custom finishing available"
    ],
    ctaLink: "/services/offset-printing"
  },
  {
    id: 3,
    title: "Custom Projects",
    description: "We are your one-stop solution for all printing needs",
    image: "https://images.unsplash.com/photo-1581077968324-53b0b672e377?w=800&q=80",
    features: [
      "Custom design services",
      "Specialty printing techniques",
      "Unique finishing options",
      "Personalized consultation"
    ],
    ctaLink: "/contact"
  }
])

const pricingPackages = ref([
  {
    id: 1,
    name: "Basic",
    price: "999",
    period: "month",
    features: [
      "Up to 1000 prints/month",
      "Standard paper options",
      "Basic design templates",
      "Email support",
      "5-day turnaround"
    ]
  },
  {
    id: 2,
    name: "Professional",
    price: "2499",
    period: "month",
    features: [
      "Up to 5000 prints/month",
      "Premium paper options",
      "Custom designs",
      "Priority support",
      "3-day turnaround",
      "Free consultation"
    ]
  },
  {
    id: 3,
    name: "Enterprise",
    price: "4999",
    period: "month",
    features: [
      "Unlimited prints",
      "All paper options",
      "Custom solutions",
      "24/7 support",
      "Next-day turnaround",
      "Dedicated account manager"
    ]
  }
])

const additionalServices = ref([
  {
    id: 1,
    title: "Design Services",
    description: "Professional design services for your printing needs",
    icon: "fas fa-paint-brush"
  },
  {
    id: 2,
    title: "Finishing Options",
    description: "Various finishing options to enhance your prints",
    icon: "fas fa-cut"
  },
  {
    id: 3,
    title: "Delivery Services",
    description: "Reliable delivery services for your printed materials",
    icon: "fas fa-truck"
  },
  {
    id: 4,
    title: "Consultation",
    description: "Expert consultation for your printing projects",
    icon: "fas fa-comments"
  }
])
</script>

<style lang="scss" scoped>
.services {
  padding-top: 80px;

  @media (max-width: 576px) {
    padding-top: 60px;
  }
}

.services-hero {
  background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url("https://images.unsplash.com/photo-1588666309990-d68f08e3d4a6?w=1920&q=80");
  background-size: cover;
  background-position: center;
  height: 40vh;
  display: flex;
  align-items: center;
  text-align: center;
  color: var(--white);

  h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
  }

  p {
    font-size: 1.2rem;
    max-width: 600px;
    margin: 0 auto;
  }

  @media (max-width: 992px) {
    height: 35vh;
    h1 { font-size: 2.5rem; }
    p { font-size: 1.1rem; }
  }

  @media (max-width: 576px) {
    height: 30vh;
    h1 { font-size: 2rem; }
    p { font-size: 1rem; }
  }
}

.section {
  padding: 4rem 0;

  @media (max-width: 992px) {
    padding: 3rem 0;
  }

  @media (max-width: 576px) {
    padding: 2rem 0;
  }
}

.section-title {
  text-align: center;
  margin-bottom: 3rem;

  h2 {
    color: var(--primary-color);
    font-size: 2.5rem;
    margin-bottom: 1rem;
  }

  p {
    color: var(--text-muted);
    max-width: 600px;
    margin: 0 auto;
  }

  @media (max-width: 992px) {
    margin-bottom: 2.5rem;
    h2 { font-size: 2.2rem; }
  }

  @media (max-width: 576px) {
    margin-bottom: 2rem;
    h2 { font-size: 1.8rem; }
  }
}

.services-grid {
  display: grid;
  gap: 4rem;
  margin-top: 2rem;

  @media (max-width: 992px) {
    gap: 3rem;
  }

  @media (max-width: 576px) {
    gap: 2rem;
    margin-top: 1rem;
  }
}

.service-item {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
  align-items: center;
  background: var(--white);
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);

  .service-image {
    height: 400px;
    overflow: hidden;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  .service-content {
    padding: 2rem;

    h3 {
      color: var(--primary-color);
      margin-bottom: 1rem;
      font-size: 1.8rem;
    }

    p {
      font-size: 1.1rem;
      line-height: 1.6;
    }

    .service-features {
      list-style: none;
      margin: 1.5rem 0;

      li {
        margin-bottom: 0.5rem;
        display: flex;
        align-items: center;
        gap: 0.5rem;
        font-size: 1.1rem;

        i {
          color: var(--secondary-color);
        }
      }
    }

    .btn {
      width: 100%;
      max-width: 200px;
    }
  }

  @media (max-width: 1200px) {
    .service-image {
      height: 350px;
    }

    .service-content {
      padding: 1.5rem;
      h3 { font-size: 1.6rem; }
      p { font-size: 1rem; }
      .service-features li { font-size: 1rem; }
    }
  }

  @media (max-width: 992px) {
    grid-template-columns: 1fr;
    
    .service-image {
      height: 300px;
    }
  }

  @media (max-width: 576px) {
    .service-image {
      height: 250px;
    }

    .service-content {
      padding: 1.25rem;
      h3 { font-size: 1.4rem; }
    }
  }
}

.pricing-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 2rem;

  @media (max-width: 992px) {
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  }

  @media (max-width: 576px) {
    gap: 1.5rem;
    margin-top: 1rem;
  }
}

.pricing-card {
  background: var(--white);
  border-radius: 8px;
  padding: 2rem;
  text-align: center;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-5px);
  }

  .package-header {
    margin-bottom: 2rem;

    h3 {
      color: var(--primary-color);
      margin-bottom: 1rem;
      font-size: 1.5rem;
    }

    .price {
      font-size: 2.5rem;
      color: var(--secondary-color);
      font-weight: 700;

      .currency {
        font-size: 1.5rem;
        vertical-align: super;
      }

      .period {
        font-size: 1rem;
        color: var(--text-muted);
      }
    }
  }

  .package-features {
    list-style: none;
    margin-bottom: 2rem;

    li {
      margin-bottom: 0.5rem;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
      font-size: 1.1rem;

      i {
        color: var(--secondary-color);
      }
    }
  }

  @media (max-width: 992px) {
    padding: 1.5rem;

    .package-header {
      h3 { font-size: 1.3rem; }
      .price { font-size: 2.2rem; }
    }

    .package-features li {
      font-size: 1rem;
    }
  }

  @media (max-width: 576px) {
    padding: 1.25rem;

    .package-header {
      margin-bottom: 1.5rem;
      .price { font-size: 2rem; }
    }
  }
}

.additional-services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-top: 2rem;

  @media (max-width: 992px) {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  }

  @media (max-width: 576px) {
    gap: 1.5rem;
    margin-top: 1rem;
    grid-template-columns: 1fr;
  }
}

.additional-service {
  text-align: center;
  padding: 2rem;
  background: var(--white);
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-5px);
  }

  .service-icon {
    font-size: 2.5rem;
    color: var(--secondary-color);
    margin-bottom: 1rem;
  }

  h3 {
    color: var(--primary-color);
    margin-bottom: 1rem;
    font-size: 1.4rem;
  }

  p {
    font-size: 1.1rem;
    line-height: 1.6;
  }

  @media (max-width: 992px) {
    padding: 1.5rem;

    .service-icon {
      font-size: 2.2rem;
    }

    h3 {
      font-size: 1.3rem;
    }

    p {
      font-size: 1rem;
    }
  }

  @media (max-width: 576px) {
    padding: 1.25rem;
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
    padding: 0 1rem;

    h2 {
      font-size: 2.5rem;
      margin-bottom: 1rem;
    }

    p {
      margin-bottom: 2rem;
      font-size: 1.2rem;
      line-height: 1.6;
    }

    .btn {
      font-size: 1.1rem;
      padding: 1rem 2rem;
    }
  }

  @media (max-width: 992px) {
    padding: 3rem 0;

    .cta-content {
      h2 {
        font-size: 2.2rem;
      }
      p {
        font-size: 1.1rem;
      }
      .btn {
        font-size: 1rem;
        padding: 0.875rem 1.75rem;
      }
    }
  }

  @media (max-width: 576px) {
    padding: 2rem 0;

    .cta-content {
      h2 {
        font-size: 1.8rem;
      }
      p {
        font-size: 1rem;
        margin-bottom: 1.5rem;
      }
      .btn {
        width: 100%;
        max-width: 250px;
      }
    }
  }
}

// Add container padding for mobile
.container {
  @media (max-width: 576px) {
    padding-left: 1rem;
    padding-right: 1rem;
  }
}

// Add smooth transitions for responsive changes
* {
  transition: all 0.3s ease;
  box-sizing: border-box;
}
</style> 