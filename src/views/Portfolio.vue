<template>
  <div class="portfolio">
    <!-- Portfolio Hero -->
    <section class="portfolio-hero">
      <div class="container">
        <h1>Our Portfolio</h1>
        <p>Explore our collection of successful printing projects</p>
      </div>
    </section>

    <!-- Portfolio Categories -->
    <section class="portfolio-categories section">
      <div class="container">
        <div class="section-title">
          <h2>Our Work</h2>
          <p>Browse through our diverse collection of printing projects</p>
        </div>
        <div class="category-filters">
          <button 
            v-for="category in categories" 
            :key="category.id"
            :class="['filter-btn', { active: selectedCategory === category.id }]"
            @click="selectedCategory = category.id"
          >
            {{ category.name }}
          </button>
        </div>
        <div class="portfolio-grid">
          <div 
            v-for="project in filteredProjects" 
            :key="project.id" 
            class="portfolio-item"
            @click="openProject(project)"
          >
            <div class="project-image">
              <img :src="project.image" :alt="project.title">
              <div class="project-overlay">
                <h3>{{ project.title }}</h3>
                <p>{{ project.category }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Testimonials -->
    <section class="testimonials section">
      <div class="container">
        <div class="section-title">
          <h2>Client Testimonials</h2>
          <p>What our clients say about our services</p>
        </div>
        <div class="testimonials-grid">
          <div class="testimonial-card" v-for="testimonial in testimonials" :key="testimonial.id">
            <div class="testimonial-content">
              <i class="fas fa-quote-left"></i>
              <p>{{ testimonial.quote }}</p>
            </div>
            <div class="testimonial-author">
              <img :src="testimonial.image" :alt="testimonial.author">
              <div class="author-info">
                <h4>{{ testimonial.author }}</h4>
                <p>{{ testimonial.position }}, {{ testimonial.company }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Project Modal -->
    <div v-if="selectedProject" class="project-modal" @click="closeProject">
      <div class="modal-content" @click.stop>
        <button class="close-btn" @click="closeProject">
          <i class="fas fa-times"></i>
        </button>
        <div class="modal-body">
          <img :src="selectedProject.image" :alt="selectedProject.title">
          <div class="project-details">
            <h2>{{ selectedProject.title }}</h2>
            <p class="category">{{ selectedProject.category }}</p>
            <p class="description">{{ selectedProject.description }}</p>
            <div class="project-info">
              <div class="info-item">
                <h4>Client</h4>
                <p>{{ selectedProject.client }}</p>
              </div>
              <div class="info-item">
                <h4>Project Type</h4>
                <p>{{ selectedProject.type }}</p>
              </div>
              <div class="info-item">
                <h4>Completion Date</h4>
                <p>{{ selectedProject.date }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const categories = ref([
  { id: 'all', name: 'All Projects' },
  { id: 'business', name: 'Business Cards' },
  { id: 'marketing', name: 'Marketing Materials' },
  { id: 'packaging', name: 'Packaging' },
  { id: 'custom', name: 'Custom Projects' }
])

const projects = ref([
  {
    id: 1,
    title: 'Corporate Business Cards',
    category: 'Business Cards',
    categoryId: 'business',
    image: 'https://images.unsplash.com/photo-1562654501-a0ccc0fc3fb1?w=800&q=80',
    description: 'Premium business cards for a leading technology company',
    client: 'Tech Solutions Inc.',
    type: 'Business Cards',
    date: 'March 2023'
  },
  {
    id: 2,
    title: 'Product Packaging',
    category: 'Packaging',
    categoryId: 'packaging',
    image: 'https://images.unsplash.com/photo-1562654435-c3c7164caa4f?w=800&q=80',
    description: 'Custom packaging design for a new product launch',
    client: 'Innovative Products Ltd.',
    type: 'Product Packaging',
    date: 'April 2023'
  },
  {
    id: 3,
    title: 'Marketing Brochures',
    category: 'Marketing Materials',
    categoryId: 'marketing',
    image: 'https://images.unsplash.com/photo-1581077968324-53b0b672e377?w=800&q=80',
    description: 'Full-color marketing brochures for a real estate company',
    client: 'Real Estate Pro',
    type: 'Marketing Materials',
    date: 'May 2023'
  },
  {
    id: 4,
    title: 'Custom Wall Art',
    category: 'Custom Projects',
    categoryId: 'custom',
    image: 'https://images.unsplash.com/photo-1561214115-f2f134cc4912?w=800&q=80',
    description: 'Large format printing for office wall art',
    client: 'Creative Design Studio',
    type: 'Custom Project',
    date: 'June 2023'
  }
])

const testimonials = ref([
  {
    id: 1,
    quote: "The best printing partner we've worked with. Their expertise and attention to detail are unmatched.",
    author: 'John Smith',
    position: 'Marketing Director',
    company: 'Tech Solutions Inc.',
    image: '/images/testimonials/client1.jpg'
  },
  {
    id: 2,
    quote: 'Professional service and outstanding results. Their attention to detail is impressive.',
    author: 'Michael Chen',
    position: 'CEO',
    company: 'Innovative Products Ltd.',
    image: '/images/testimonials/michael-chen.jpg'
  },
  {
    id: 3,
    quote: "The best printing partner we've worked with. Their expertise and customer service are unmatched.",
    author: 'Emily Davis',
    position: 'Creative Director',
    company: 'Real Estate Pro',
    image: '/images/testimonials/emily-davis.jpg'
  }
])

const selectedCategory = ref('all')
const selectedProject = ref(null)

const filteredProjects = computed(() => {
  if (selectedCategory.value === 'all') {
    return projects.value
  }
  return projects.value.filter(project => project.categoryId === selectedCategory.value)
})

const openProject = (project) => {
  selectedProject.value = project
}

const closeProject = () => {
  selectedProject.value = null
}
</script>

<style lang="scss" scoped>
.portfolio {
  padding-top: 80px;
}

.portfolio-hero {
  background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://images.unsplash.com/photo-1588666309990-d68f08e3d4a6?w=1920&q=80');
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
}

.category-filters {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 2rem;
  flex-wrap: wrap;

  .filter-btn {
    padding: 0.5rem 1.5rem;
    border: none;
    background: var(--white);
    border-radius: 25px;
    cursor: pointer;
    transition: all 0.3s ease;
    font-weight: 500;

    &:hover {
      background: var(--primary-color);
      color: var(--white);
    }

    &.active {
      background: var(--primary-color);
      color: var(--white);
    }
  }
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

.portfolio-item {
  cursor: pointer;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-5px);

    .project-overlay {
      opacity: 1;
    }
  }

  .project-image {
    position: relative;
    height: 300px;
    overflow: hidden;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.3s ease;
    }

    .project-overlay {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(0,0,0,0.7);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      color: var(--white);
      opacity: 0;
      transition: opacity 0.3s ease;

      h3 {
        font-size: 1.5rem;
        margin-bottom: 0.5rem;
      }
    }
  }
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.testimonial-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);

  .testimonial-content {
    margin-bottom: 1.5rem;

    i {
      color: var(--secondary-color);
      font-size: 2rem;
      margin-bottom: 1rem;
    }

    p {
      font-style: italic;
      line-height: 1.6;
    }
  }

  .testimonial-author {
    display: flex;
    align-items: center;
    gap: 1rem;

    img {
      width: 60px;
      height: 60px;
      border-radius: 50%;
      object-fit: cover;
    }

    .author-info {
      h4 {
        color: var(--primary-color);
        margin-bottom: 0.25rem;
      }

      p {
        color: #666;
        font-size: 0.9rem;
      }
    }
  }
}

.project-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0,0,0,0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;

  .modal-content {
    background: var(--white);
    width: 90%;
    max-width: 1000px;
    max-height: 90vh;
    border-radius: 8px;
    position: relative;
    overflow-y: auto;

    .close-btn {
      position: absolute;
      top: 1rem;
      right: 1rem;
      background: none;
      border: none;
      font-size: 1.5rem;
      cursor: pointer;
      color: var(--primary-color);
      z-index: 1;
    }

    .modal-body {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
      padding: 2rem;

      img {
        width: 100%;
        height: auto;
        border-radius: 8px;
      }

      .project-details {
        h2 {
          color: var(--primary-color);
          margin-bottom: 0.5rem;
        }

        .category {
          color: var(--secondary-color);
          font-weight: 500;
          margin-bottom: 1rem;
        }

        .description {
          margin-bottom: 2rem;
        }

        .project-info {
          display: grid;
          grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
          gap: 1rem;

          .info-item {
            h4 {
              color: var(--primary-color);
              margin-bottom: 0.5rem;
            }

            p {
              color: #666;
            }
          }
        }
      }
    }
  }
}

@media (max-width: 768px) {
  .portfolio-hero h1 {
    font-size: 2.5rem;
  }

  .project-modal .modal-body {
    grid-template-columns: 1fr;
  }
}
</style> 