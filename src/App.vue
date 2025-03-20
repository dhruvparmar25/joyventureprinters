<template>
  <div class="app">
    <nav class="navbar">
      <div class="container">
        <router-link to="/" class="logo">
          JoyVenture Printers
        </router-link>
        <button class="mobile-menu-toggle" @click="isMenuOpen = !isMenuOpen">
          <i :class="['fas', isMenuOpen ? 'fa-times' : 'fa-bars']"></i>
        </button>
        <div :class="['nav-links', { 'is-open': isMenuOpen }]">
          <router-link to="/" class="nav-link" @click="isMenuOpen = false">Home</router-link>
          <router-link to="/about" class="nav-link" @click="isMenuOpen = false">About</router-link>
          <router-link to="/services" class="nav-link" @click="isMenuOpen = false">Services</router-link>
          <router-link to="/portfolio" class="nav-link" @click="isMenuOpen = false">Portfolio</router-link>
          <router-link to="/contact" class="nav-link" @click="isMenuOpen = false">Contact</router-link>
          <router-link to="/faq" class="nav-link" @click="isMenuOpen = false">FAQ</router-link>
          <router-link to="/blog" class="nav-link" @click="isMenuOpen = false">Blog</router-link>
        </div>
      </div>
    </nav>

    <router-view v-slot="{ Component }">
      <transition name="fade" mode="out-in">
        <component :is="Component" />
      </transition>
    </router-view>

    <footer class="footer">
      <div class="container">
        <div class="footer-content">
          <div class="footer-section">
            <h3>JoyVenture Printers</h3>
            <p>Your trusted partner for all printing needs</p>
          </div>
          <div class="footer-section">
            <h3>Quick Links</h3>
            <router-link to="/services">Services</router-link>
            <router-link to="/portfolio">Portfolio</router-link>
            <router-link to="/contact">Contact</router-link>
          </div>
          <div class="footer-section">
            <h3>Contact Info</h3>
            <p>Email: info@joyventureprinters.com</p>
            <p>Phone: +1234567890</p>
            <p>Address: Your Business Address</p>
          </div>
        </div>
        <div class="footer-bottom">
          <p>&copy; {{ new Date().getFullYear() }} JoyVenture Printers. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const isMenuOpen = ref(false)
</script>

<style lang="scss">
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.navbar {
  background-color: #ffffff;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 1000;

  .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 20px;
    position: relative;
  }

  .logo {
    font-size: 1.5rem;
    font-weight: 700;
    color: #2563eb;
    text-decoration: none;
    transition: color 0.3s ease;

    &:hover {
      color: #1d4ed8;
    }
  }

  .mobile-menu-toggle {
    display: none;
    background: none;
    border: none;
    color: #2563eb;
    font-size: 1.5rem;
    cursor: pointer;
    padding: 0.5rem;
    transition: all 0.3s ease;

    &:hover {
      color: #1d4ed8;
      transform: scale(1.1);
    }
  }

  .nav-links {
    display: flex;
    gap: 2rem;

    .nav-link {
      color: #4b5563;
      text-decoration: none;
      font-weight: 500;
      padding: 0.5rem 1rem;
      border-radius: 0.375rem;
      transition: all 0.3s ease;

      &:hover {
        color: #2563eb;
        background-color: #f3f4f6;
      }

      &.router-link-active {
        color: #2563eb;
        background-color: #eff6ff;
      }
    }
  }

  @media (max-width: 992px) {
    .mobile-menu-toggle {
      display: block;
    }

    .nav-links {
      display: none;
      position: absolute;
      top: 100%;
      left: 0;
      right: 0;
      flex-direction: column;
      gap: 0;
      background-color: #ffffff;
      box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
      padding: 0.5rem 0;
      text-align: center;
      border-bottom-left-radius: 0.5rem;
      border-bottom-right-radius: 0.5rem;

      &.is-open {
        display: flex;
        animation: slideDown 0.3s ease-out forwards;
      }

      .nav-link {
        padding: 1rem;
        display: block;
        border-radius: 0;
        border-bottom: 1px solid #e5e7eb;
        margin: 0;
        transition: all 0.3s ease;

        &:hover {
          color: #2563eb;
          background-color: #f3f4f6;
        }

        &.router-link-active {
          color: #2563eb;
          background-color: #eff6ff;
        }

        &:last-child {
          border-bottom: none;
        }
      }
    }
  }
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.footer {
  background-color: var(--primary-color);
  color: var(--white);
  padding: 4rem 0 2rem;
  margin-top: auto;

  .footer-content {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    margin-bottom: 2rem;
  }

  .footer-section {
    h3 {
      margin-bottom: 1rem;
      font-size: 1.2rem;
    }

    a {
      color: var(--white);
      text-decoration: none;
      display: block;
      margin-bottom: 0.5rem;
      opacity: 0.8;
      transition: opacity 0.3s ease;

      &:hover {
        opacity: 1;
      }
    }
  }

  .footer-bottom {
    text-align: center;
    padding-top: 2rem;
    border-top: 1px solid rgba(255,255,255,0.1);
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style> 