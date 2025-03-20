<template>
  <div class="blog-post">
    <section class="post-hero">
      <div class="container">
        <div class="post-meta">
          <span class="date">{{ post.date }}</span>
          <span class="category">{{ post.category }}</span>
        </div>
        <h1>{{ post.title }}</h1>
        <p class="excerpt">{{ post.excerpt }}</p>
      </div>
    </section>

    <section class="post-content section">
      <div class="container">
        <div class="post-image">
          <img :src="post.image" :alt="post.title">
        </div>
        <div class="content">
          <p>{{ post.content }}</p>
          <h2>Key Takeaways</h2>
          <ul>
            <li v-for="(point, index) in post.keyPoints" :key="index">
              {{ point }}
            </li>
          </ul>
        </div>
      </div>
    </section>

    <section class="related-posts section">
      <div class="container">
        <h2>Related Posts</h2>
        <div class="posts-grid">
          <article v-for="relatedPost in relatedPosts" :key="relatedPost.id" class="post-card">
            <div class="post-image">
              <img :src="relatedPost.image" :alt="relatedPost.title">
            </div>
            <div class="post-content">
              <h3>{{ relatedPost.title }}</h3>
              <p>{{ relatedPost.excerpt }}</p>
              <router-link :to="'/blog/' + relatedPost.id" class="read-more">
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
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const post = ref({
  id: 1,
  title: 'The Future of Digital Printing',
  excerpt: 'Explore the latest trends and innovations in digital printing technology.',
  date: 'March 15, 2024',
  category: 'Technology',
  image: '/images/blog/digital-printing.jpg',
  content: 'Digital printing technology continues to evolve at a rapid pace, bringing new possibilities and efficiencies to the industry. From advanced color management systems to automated workflow solutions, the future of digital printing looks promising.',
  keyPoints: [
    'Advanced color management systems',
    'Automated workflow solutions',
    'Improved print quality',
    'Faster turnaround times',
    'Cost-effective solutions'
  ]
})

const relatedPosts = ref([
  {
    id: 2,
    title: 'Choosing the Right Paper for Your Project',
    excerpt: 'A comprehensive guide to selecting the perfect paper for your printing needs.',
    image: '/images/blog/paper-guide.jpg'
  },
  {
    id: 3,
    title: 'Sustainable Printing Practices',
    excerpt: "Learn how we're making printing more environmentally friendly.",
    image: '/images/blog/sustainable-printing.jpg'
  }
])

onMounted(() => {
  // Here you would typically fetch the post data based on the route parameter
  const postId = parseInt(route.params.id)
  // Fetch post data from your API
})
</script>

<style lang="scss" scoped>
.blog-post {
  padding-top: 80px;
}

.post-hero {
  background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('/images/blog-hero.jpg');
  background-size: cover;
  background-position: center;
  height: 50vh;
  display: flex;
  align-items: center;
  text-align: center;
  color: var(--white);

  .post-meta {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-bottom: 1rem;
    font-size: 0.9rem;
  }

  h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
  }

  .excerpt {
    font-size: 1.2rem;
    max-width: 800px;
    margin: 0 auto;
  }
}

.post-content {
  .post-image {
    margin-bottom: 2rem;
    border-radius: 8px;
    overflow: hidden;

    img {
      width: 100%;
      height: auto;
      display: block;
    }
  }

  .content {
    max-width: 800px;
    margin: 0 auto;

    p {
      margin-bottom: 2rem;
      line-height: 1.8;
    }

    h2 {
      color: var(--primary-color);
      margin-bottom: 1rem;
    }

    ul {
      list-style: none;
      padding: 0;

      li {
        margin-bottom: 0.5rem;
        padding-left: 1.5rem;
        position: relative;

        &:before {
          content: '•';
          color: var(--secondary-color);
          position: absolute;
          left: 0;
        }
      }
    }
  }
}

.related-posts {
  background-color: var(--light-bg);

  h2 {
    text-align: center;
    color: var(--primary-color);
    margin-bottom: 2rem;
  }
}

.posts-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.post-card {
  background: var(--white);
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-5px);
  }

  .post-image {
    height: 200px;
    overflow: hidden;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  .post-content {
    padding: 1.5rem;

    h3 {
      color: var(--primary-color);
      margin-bottom: 1rem;
      font-size: 1.5rem;
    }

    p {
      margin-bottom: 1rem;
      color: #666;
    }

    .read-more {
      color: var(--secondary-color);
      text-decoration: none;
      font-weight: 500;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;

      &:hover {
        color: var(--primary-color);
      }
    }
  }
}

@media (max-width: 768px) {
  .post-hero {
    h1 {
      font-size: 2.5rem;
    }
  }
}
</style> 