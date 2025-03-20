<template>
  <div class="faq">
    <section class="faq-hero">
      <div class="container">
        <h1>Frequently Asked Questions</h1>
        <p>Find answers to common questions about our printing services</p>
      </div>
    </section>

    <section class="faq-content section">
      <div class="container">
        <div class="faq-grid">
          <div v-for="faq in faqs" :key="faq.id" class="faq-item">
            <div class="faq-question" @click="toggleFaq(faq.id)">
              <h3>{{ faq.question }}</h3>
              <i :class="['fas', expandedFaq === faq.id ? 'fa-chevron-up' : 'fa-chevron-down']"></i>
            </div>
            <div class="faq-answer" v-show="expandedFaq === faq.id">
              <p>{{ faq.answer }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const expandedFaq = ref(null)

const faqs = ref([
  {
    id: 1,
    question: "What types of printing services do you offer?",
    answer: "We offer a wide range of printing services including digital printing, offset printing, large format printing, and custom projects. Our services cover everything from business cards to large banners and everything in between."
  },
  {
    id: 2,
    question: "What is your typical turnaround time?",
    answer: "Turnaround times vary depending on the project type and complexity. Digital printing typically takes 1-3 business days, while offset printing may take 5-10 business days. Rush services are available for urgent projects."
  },
  {
    id: 3,
    question: "Do you provide design services?",
    answer: "Yes, we offer professional design services through our in-house design team. We can help create or modify designs for your printing projects, ensuring they meet industry standards and your specific requirements."
  },
  {
    id: 4,
    question: "What file formats do you accept?",
    answer: "We accept all major file formats including PDF, AI, PSD, and EPS. For best results, we recommend submitting files in PDF format with proper bleed and crop marks."
  },
  {
    id: 5,
    question: "Do you offer bulk printing discounts?",
    answer: "Yes, we offer competitive pricing for bulk orders. The more you order, the more you save. Contact us for a custom quote based on your specific needs."
  }
])

const toggleFaq = (id) => {
  expandedFaq.value = expandedFaq.value === id ? null : id
}
</script>

<style lang="scss" scoped>
.faq {
  padding-top: 80px;
}

.faq-hero {
  background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://via.placeholder.com/1920x1080');
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

.faq-grid {
  max-width: 800px;
  margin: 0 auto;
}

.faq-item {
  margin-bottom: 1rem;
  border: 1px solid var(--border-color);
  border-radius: 8px;
  overflow: hidden;
}

.faq-question {
  padding: 1.5rem;
  background-color: var(--white);
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;

  h3 {
    margin: 0;
    color: var(--primary-color);
  }

  i {
    color: var(--secondary-color);
    transition: transform 0.3s ease;
  }

  &:hover {
    background-color: var(--light-bg);
  }
}

.faq-answer {
  padding: 0 1.5rem 1.5rem;
  background-color: var(--white);
  color: var(--text-color);
}

@media (max-width: 768px) {
  .faq-hero h1 {
    font-size: 2.5rem;
  }
}
</style> 