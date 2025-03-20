<template>
  <div class="about">
    <!-- About Hero -->
    <section class="about-hero">
      <div class="container">
        <h1>About JoyVenture Printers</h1>
        <p>Your trusted partner in professional printing solutions</p>
      </div>
    </section>

    <!-- Company Story -->
    <section class="company-story section">
      <div class="container">
        <div class="story-content">
          <div class="story-text">
            <h2>Our Story</h2>
            <p>Founded in 2010, JoyVenture Printers has been at the forefront of the printing industry, providing innovative solutions to businesses and individuals alike. What started as a small local print shop has grown into a full-service printing company serving clients nationwide.</p>
            <p>Our journey has been marked by continuous innovation, investment in cutting-edge technology, and an unwavering commitment to customer satisfaction. We believe in building lasting relationships with our clients by delivering exceptional quality and service.</p>
          </div>
          <div class="story-image">
            <img src="https://via.placeholder.com/800x600" alt="Our Printing Facility">
          </div>
        </div>
      </div>
    </section>

    <!-- Mission & Vision -->
    <section class="mission-vision section">
      <div class="container">
        <div class="mission-vision-grid">
          <div class="mission">
            <h2>Our Mission</h2>
            <p>To provide high-quality printing solutions that help businesses and individuals achieve their goals through exceptional service, innovative technology, and sustainable practices.</p>
          </div>
          <div class="vision">
            <h2>Our Vision</h2>
            <p>To be the leading printing solutions provider, recognized for our commitment to quality, innovation, and customer satisfaction.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Team Section -->
    <section class="team section">
      <div class="container">
        <div class="section-title">
          <h2>Our Team</h2>
          <p>Meet the dedicated professionals behind our success</p>
        </div>
        <div class="team-grid">
          <div class="team-member" v-for="member in team" :key="member.id">
            <div class="member-image">
              <img :src="member.image" :alt="member.name">
            </div>
            <div class="member-info">
              <h3>{{ member.name }}</h3>
              <p class="position">{{ member.position }}</p>
              <p class="bio">{{ member.bio }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Values Section -->
    <section class="values section">
      <div class="container">
        <div class="section-title">
          <h2>Our Values</h2>
          <p>The principles that guide everything we do</p>
        </div>
        <div class="values-grid">
          <div class="value-card" v-for="value in values" :key="value.id">
            <div class="value-icon">
              <i :class="value.icon"></i>
            </div>
            <h3>{{ value.title }}</h3>
            <p>{{ value.description }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const team = ref([
  {
    id: 1,
    name: 'John Doe',
    position: 'CEO & Founder',
    bio: 'With over 20 years of experience in the printing industry, John leads our team with vision and expertise.',
    image: 'https://images.unsplash.com/photo-1560250097-0b93528c311a?w=400&q=80'
  },
  {
    id: 2,
    name: 'Jane Smith',
    position: 'Operations Manager',
    bio: 'Jane ensures smooth operations and maintains our high quality standards.',
    image: 'https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?w=400&q=80'
  },
  {
    id: 3,
    name: 'Mike Johnson',
    position: 'Technical Director',
    bio: 'Mike oversees our technical operations and keeps us at the cutting edge of printing technology.',
    image: 'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?w=400&q=80'
  }
])

const values = ref([
  {
    id: 1,
    title: 'Quality',
    description: 'We never compromise on quality, ensuring every print meets our high standards.',
    icon: 'fas fa-star'
  },
  {
    id: 2,
    title: 'Innovation',
    description: 'We continuously invest in new technology and methods to improve our services.',
    icon: 'fas fa-lightbulb'
  },
  {
    id: 3,
    title: 'Sustainability',
    description: "We're committed to environmentally responsible printing practices.",
    icon: 'fas fa-leaf'
  },
  {
    id: 4,
    title: 'Customer Focus',
    description: "Our customers' satisfaction is our top priority.",
    icon: 'fas fa-heart'
  }
])
</script>

<style lang="scss" scoped>
.about {
  padding-top: 80px;
}

.about-hero {
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

.company-story {
  .story-content {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;

    .story-text {
      h2 {
        color: var(--primary-color);
        margin-bottom: 1.5rem;
      }

      p {
        margin-bottom: 1rem;
      }
    }

    .story-image {
      img {
        width: 100%;
        border-radius: 8px;
        box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      }
    }
  }
}

.mission-vision {
  background-color: var(--light-bg);

  .mission-vision-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;

    h2 {
      color: var(--primary-color);
      margin-bottom: 1.5rem;
    }
  }
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.team-member {
  background: var(--white);
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-5px);
  }

  .member-image {
    height: 300px;
    overflow: hidden;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  .member-info {
    padding: 1.5rem;

    h3 {
      color: var(--primary-color);
      margin-bottom: 0.5rem;
    }

    .position {
      color: var(--secondary-color);
      font-weight: 500;
      margin-bottom: 1rem;
    }
  }
}

.values-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.value-card {
  text-align: center;
  padding: 2rem;
  background: var(--white);
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);

  .value-icon {
    font-size: 2.5rem;
    color: var(--secondary-color);
    margin-bottom: 1rem;
  }

  h3 {
    color: var(--primary-color);
    margin-bottom: 1rem;
  }
}

@media (max-width: 768px) {
  .company-story .story-content,
  .mission-vision .mission-vision-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .about-hero h1 {
    font-size: 2.5rem;
  }
}
</style> 