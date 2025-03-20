<template>
  <div class="digital-printing">
    <section class="service-hero">
      <div class="container">
        <h1>Digital Printing Services</h1>
        <p>High-quality digital prints for small to medium runs</p>
      </div>
    </section>

    <section class="service-details section">
      <div class="container">
        <div class="service-content">
          <div class="service-image">
            <img src="https://images.unsplash.com/photo-1562654501-a0ccc0fc3fb1?w=800&q=80" alt="Digital Printing">
          </div>
          <div class="service-info">
            <h2>Digital Printing Solutions</h2>
            <p>Our digital printing services offer high-quality results with quick turnaround times, perfect for small to medium print runs.</p>
            
            <div class="features">
              <h3>Key Features</h3>
              <ul>
                <li><i class="fas fa-check"></i> Full-color printing with vibrant results</li>
                <li><i class="fas fa-check"></i> Variable data printing capabilities</li>
                <li><i class="fas fa-check"></i> Quick turnaround times</li>
                <li><i class="fas fa-check"></i> Cost-effective for small runs</li>
                <li><i class="fas fa-check"></i> High-quality paper options</li>
                <li><i class="fas fa-check"></i> Custom finishing available</li>
              </ul>
            </div>

            <div class="applications">
              <h3>Common Applications</h3>
              <ul>
                <li>Business cards</li>
                <li>Marketing materials</li>
                <li>Event materials</li>
                <li>Direct mail campaigns</li>
                <li>Product catalogs</li>
                <li>Brochures and flyers</li>
              </ul>
            </div>

            <router-link to="/contact" class="btn btn-primary">Get a Quote</router-link>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
// Component logic here
</script>

<style lang="scss" scoped>
.digital-printing {
  padding-top: 80px;
}

.service-hero {
  background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://images.unsplash.com/photo-1562654501-a0ccc0fc3fb1?w=1920&q=80');
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

.service-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}

.service-image {
  img {
    width: 100%;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  }
}

.service-info {
  h2 {
    color: var(--primary-color);
    margin-bottom: 1.5rem;
  }

  .features, .applications {
    margin: 2rem 0;

    h3 {
      color: var(--secondary-color);
      margin-bottom: 1rem;
    }

    ul {
      list-style: none;
      padding: 0;

      li {
        margin-bottom: 0.5rem;
        display: flex;
        align-items: center;
        gap: 0.5rem;

        i {
          color: var(--secondary-color);
        }
      }
    }
  }

  .btn {
    margin-top: 2rem;
  }
}

@media (max-width: 768px) {
  .service-content {
    grid-template-columns: 1fr;
  }

  .service-hero h1 {
    font-size: 2.5rem;
  }
}
</style> 