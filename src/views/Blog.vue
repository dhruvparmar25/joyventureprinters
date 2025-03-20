<template>
  <div class="blog">
    <section class="blog-hero">
      <div class="container">
        <h1>Printing Insights & Tips</h1>
        <p>Stay updated with the latest printing trends and industry knowledge</p>
      </div>
    </section>

    <section class="blog-content section">
      <div class="container">
        <div class="blog-grid">
          <article v-for="post in blogPosts" :key="post.id" class="blog-card">
            <div class="blog-image">
              <img :src="post.image" :alt="post.title">
            </div>
            <div class="blog-info">
              <div class="blog-meta">
                <span class="date">{{ post.date }}</span>
                <span class="category">{{ post.category }}</span>
              </div>
              <h2>{{ post.title }}</h2>
              <p>{{ post.excerpt }}</p>
              <router-link :to="'/blog/' + post.slug" class="read-more">
                Read More <i class="fas fa-arrow-right"></i>
              </router-link>
            </div>
          </article>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const blogPosts = ref([
  {
    id: 1,
    title: "The Future of Digital Printing Technology",
    excerpt: "Explore the latest advancements in digital printing and how they're shaping the industry.",
    image: "https://images.unsplash.com/photo-1562654501-a0ccc0fc3fb1?w=800&q=80",
    date: "March 15, 2024",
    category: "Technology",
    slug: "future-digital-printing"
  },
  {
    id: 2,
    title: "Choosing the Right Paper for Your Project",
    excerpt: "A comprehensive guide to selecting the perfect paper type for your printing needs.",
    image: "https://images.unsplash.com/photo-1562654435-c3c7164caa4f?w=800&q=80",
    date: "March 10, 2024",
    category: "Tips & Guides",
    slug: "choosing-right-paper"
  },
  {
    id: 3,
    title: "Sustainable Printing Practices",
    excerpt: "Learn how eco-friendly printing solutions can benefit your business and the environment.",
    image: "https://images.unsplash.com/photo-1581077968324-53b0b672e377?w=800&q=80",
    date: "March 5, 2024",
    category: "Sustainability",
    slug: "sustainable-printing"
  }
])
</script>

<style lang="scss" scoped>
.blog {
  padding-top: 80px;
}

.blog-hero {
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

.blog-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.blog-card {
  background: var(--white);
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-5px);
  }

  .blog-image {
    img {
      width: 100%;
      height: 200px;
      object-fit: cover;
    }
  }

  .blog-info {
    padding: 1.5rem;

    .blog-meta {
      display: flex;
      gap: 1rem;
      margin-bottom: 1rem;
      color: var(--text-muted);
      font-size: 0.9rem;

      .category {
        color: var(--secondary-color);
        font-weight: 500;
      }
    }

    h2 {
      color: var(--primary-color);
      margin-bottom: 1rem;
      font-size: 1.5rem;
    }

    p {
      color: var(--text-color);
      margin-bottom: 1.5rem;
    }

    .read-more {
      color: var(--secondary-color);
      text-decoration: none;
      font-weight: 500;
      display: flex;
      align-items: center;
      gap: 0.5rem;

      &:hover {
        text-decoration: underline;
      }
    }
  }
}

@media (max-width: 768px) {
  .blog-hero h1 {
    font-size: 2.5rem;
  }
}
</style> 