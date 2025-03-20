<template>
  <div class="contact">
    <!-- Contact Hero -->
    <section class="contact-hero">
      <div class="container">
        <h1>Contact Us</h1>
        <p>Get in touch with us for your printing needs</p>
      </div>
    </section>

    <!-- Contact Information -->
    <section class="contact-info section">
      <div class="container">
        <div class="contact-grid">
          <div class="info-card">
            <div class="icon">
              <i class="fas fa-map-marker-alt"></i>
            </div>
            <h3>Address</h3>
            <p>123 Printing Street</p>
            <p>Business District</p>
            <p>City, State 12345</p>
          </div>
          <div class="info-card">
            <div class="icon">
              <i class="fas fa-phone"></i>
            </div>
            <h3>Phone</h3>
            <p>+1 (234) 567-8900</p>
            <p>+1 (234) 567-8901</p>
          </div>
          <div class="info-card">
            <div class="icon">
              <i class="fas fa-envelope"></i>
            </div>
            <h3>Email</h3>
            <p>info@joyventureprinters.com</p>
            <p>support@joyventureprinters.com</p>
          </div>
          <div class="info-card">
            <div class="icon">
              <i class="fas fa-clock"></i>
            </div>
            <h3>Business Hours</h3>
            <p>Monday - Friday: 9:00 AM - 6:00 PM</p>
            <p>Saturday: 10:00 AM - 4:00 PM</p>
            <p>Sunday: Closed</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Form and Map -->
    <section class="contact-form-map section">
      <div class="container">
        <div class="form-map-grid">
          <div class="contact-form">
            <h2>Send us a Message</h2>
            <form @submit.prevent="submitForm">
              <div class="form-group">
                <label for="name">Name</label>
                <input 
                  type="text" 
                  id="name" 
                  v-model="form.name" 
                  required
                  placeholder="Your name"
                >
              </div>
              <div class="form-group">
                <label for="email">Email</label>
                <input 
                  type="email" 
                  id="email" 
                  v-model="form.email" 
                  required
                  placeholder="Your email"
                >
              </div>
              <div class="form-group">
                <label for="phone">Phone</label>
                <input 
                  type="tel" 
                  id="phone" 
                  v-model="form.phone"
                  placeholder="Your phone number"
                >
              </div>
              <div class="form-group">
                <label for="subject">Subject</label>
                <input 
                  type="text" 
                  id="subject" 
                  v-model="form.subject" 
                  required
                  placeholder="Message subject"
                >
              </div>
              <div class="form-group">
                <label for="message">Message</label>
                <textarea 
                  id="message" 
                  v-model="form.message" 
                  required
                  rows="5"
                  placeholder="Your message"
                ></textarea>
              </div>
              <button type="submit" class="btn btn-primary">
                Send Message
              </button>
            </form>
          </div>
          <div class="map-container">
            <iframe
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d387193.30591910525!2d-74.25986532945684!3d40.69714941966631!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x89c24fa5d33f083b%3A0xc80b8f06e177fe62!2sNew%20York%2C%20NY%2C%20USA!5e0!3m2!1sen!2s!4v1641234567890!5m2!1sen!2s"
              width="100%"
              height="450"
              style="border:0;"
              allowfullscreen=""
              loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"
            ></iframe>
          </div>
        </div>
      </div>
    </section>

    <!-- FAQ Section -->
    <section class="faq-section section">
      <div class="container">
        <div class="section-title">
          <h2>Frequently Asked Questions</h2>
          <p>Find answers to common questions about our services</p>
        </div>
        <div class="faq-grid">
          <div class="faq-item" v-for="faq in faqs" :key="faq.id">
            <div class="faq-question" @click="toggleFaq(faq.id)">
              <h3>{{ faq.question }}</h3>
              <i :class="['fas', faq.isOpen ? 'fa-chevron-up' : 'fa-chevron-down']"></i>
            </div>
            <div class="faq-answer" v-show="faq.isOpen">
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

const form = ref({
  name: '',
  email: '',
  phone: '',
  subject: '',
  message: ''
})

const faqs = ref([
  {
    id: 1,
    question: 'What types of printing services do you offer?',
    answer: 'We offer a wide range of printing services including digital printing, offset printing, large format printing, and custom printing solutions.',
    isOpen: false
  },
  {
    id: 2,
    question: 'What is your typical turnaround time?',
    answer: 'Turnaround times vary depending on the project. Standard orders typically take 3-5 business days, while rush orders can be completed in 24-48 hours.',
    isOpen: false
  },
  {
    id: 3,
    question: 'Do you offer design services?',
    answer: 'Yes, we have an in-house design team that can help create custom designs for your printing projects.',
    isOpen: false
  },
  {
    id: 4,
    question: 'What file formats do you accept?',
    answer: 'We accept all major file formats including PDF, AI, PSD, and JPG. For best results, we recommend submitting files in PDF format.',
    isOpen: false
  }
])

const submitForm = () => {
  // Here you would typically send the form data to your backend
  console.log('Form submitted:', form.value)
  // Reset form
  form.value = {
    name: '',
    email: '',
    phone: '',
    subject: '',
    message: ''
  }
}

const toggleFaq = (id) => {
  const faq = faqs.value.find(f => f.id === id)
  if (faq) {
    faq.isOpen = !faq.isOpen
  }
}
</script>

<style lang="scss" scoped>
.contact {
  padding-top: 80px;
}

.contact-hero {
  background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('/images/contact-hero.jpg');
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

.contact-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.info-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 8px;
  text-align: center;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);

  .icon {
    font-size: 2rem;
    color: var(--secondary-color);
    margin-bottom: 1rem;
  }

  h3 {
    color: var(--primary-color);
    margin-bottom: 1rem;
  }

  p {
    margin-bottom: 0.5rem;
    color: #666;
  }
}

.form-map-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  margin-top: 2rem;
}

.contact-form {
  h2 {
    color: var(--primary-color);
    margin-bottom: 2rem;
  }

  .form-group {
    margin-bottom: 1.5rem;

    label {
      display: block;
      margin-bottom: 0.5rem;
      color: var(--primary-color);
      font-weight: 500;
    }

    input,
    textarea {
      width: 100%;
      padding: 0.75rem;
      border: 1px solid #ddd;
      border-radius: 4px;
      font-size: 1rem;

      &:focus {
        outline: none;
        border-color: var(--primary-color);
      }
    }
  }
}

.map-container {
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.faq-grid {
  max-width: 800px;
  margin: 2rem auto 0;
}

.faq-item {
  background: var(--white);
  border-radius: 8px;
  margin-bottom: 1rem;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  overflow: hidden;

  .faq-question {
    padding: 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;

    h3 {
      color: var(--primary-color);
      margin: 0;
    }

    i {
      color: var(--secondary-color);
    }
  }

  .faq-answer {
    padding: 0 1.5rem 1.5rem;
    color: #666;
  }
}

@media (max-width: 768px) {
  .contact-hero h1 {
    font-size: 2.5rem;
  }

  .form-map-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
}
</style> 