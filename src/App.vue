<template>
  <div class="app">
    <nav class="navbar">
      <div class="container">
        <router-link to="/" class="logo">
          JoyVenture Printers
        </router-link>
        
        <button class="mobile-menu-toggle" @click="toggleMenu" aria-label="Toggle menu">
          <i :class="isMenuOpen ? 'fas fa-times' : 'fas fa-bars'"></i>
        </button>

        <div :class="['nav-links', { 'is-open': isMenuOpen }]">
          <router-link to="/" class="nav-link" @click="closeMenu">Home</router-link>
          <router-link to="/about" class="nav-link" @click="closeMenu">About</router-link>
          <router-link to="/services" class="nav-link" @click="closeMenu">Services</router-link>
          <router-link to="/portfolio" class="nav-link" @click="closeMenu">Portfolio</router-link>
          <router-link to="/contact" class="nav-link" @click="closeMenu">Contact</router-link>
          <router-link to="/faq" class="nav-link" @click="closeMenu">FAQ</router-link>
          <router-link to="/blog" class="nav-link" @click="closeMenu">Blog</router-link>
        </div>
      </div>
    </nav>

    <router-view v-slot="{ Component }">
      <transition name="fade" mode="out-in">
        <component :is="Component" />
      </transition>
    </router-view>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const isMenuOpen = ref(false)
const toggleMenu = () => { isMenuOpen.value = !isMenuOpen.value }
const closeMenu = () => { isMenuOpen.value = false }
</script>

<style lang="scss">
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.navbar {
  background-color: #ffffff;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
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
  }

  .mobile-menu-toggle {
    display: none;
    background: none;
    border: none;
    padding: 8px;
    cursor: pointer;
    color: #2563eb;
    z-index: 1002;
    
    i {
      font-size: 24px;
    }

    &:hover {
      color: darken(#2563eb, 10%);
    }
  }

  .nav-links {
    display: flex;
    gap: 2rem;
    align-items: center;

    .nav-link {
      color: #4b5563;
      text-decoration: none;
      font-weight: 500;
      padding: 0.5rem 1rem;
      transition: color 0.3s ease;

      &:hover {
        color: #2563eb;
      }
    }
  }

  @media (max-width: 992px) {
    .mobile-menu-toggle {
      display: block;
      position: absolute;
      right: 20px;
      top: 50%;
      transform: translateY(-50%);
      background-color: #f3f4f6;
      border-radius: 8px;
      padding: 12px;
      
      i {
        display: block;
        line-height: 1;
      }
    }

    .nav-links {
      display: none;
      flex-direction: column;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100vh;
      background: rgba(255, 255, 255, 0.98);
      padding: 80px 20px 20px;
      gap: 1rem;
      align-items: center;
      justify-content: flex-start;
      z-index: 1001;

      &.is-open {
        display: flex;
      }

      .nav-link {
        font-size: 1.2rem;
        padding: 1rem;
        width: 100%;
        text-align: center;
        border-radius: 8px;

        &:hover {
          background-color: #f3f4f6;
        }
      }
    }
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