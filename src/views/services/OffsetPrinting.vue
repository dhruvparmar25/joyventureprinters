<template>
  <div class="offset-printing">
    <section class="service-hero">
      <div class="container">
        <h1>Offset Printing Services</h1>
        <p>Professional offset printing for large volume projects</p>
      </div>
    </section>

    <section class="service-details section">
      <div class="container">
        <div class="service-content">
          <div class="service-image">
            <img src="https://images.unsplash.com/photo-1562654435-c3c7164caa4f?w=800&q=80" alt="Offset Printing">
          </div>
          <div class="service-info">
            <h2>Offset Printing Solutions</h2>
            <p>Our offset printing services deliver superior quality results for large volume projects, offering excellent value and consistency.</p>
            
            <div class="features">
              <h3>Key Features</h3>
              <ul>
                <li><i class="fas fa-check"></i> High-quality results with precise color matching</li>
                <li><i class="fas fa-check"></i> Cost-effective for large print runs</li>
                <li><i class="fas fa-check"></i> Wide range of paper options and finishes</li>
                <li><i class="fas fa-check"></i> Custom finishing and binding options</li>
                <li><i class="fas fa-check"></i> Pantone color matching available</li>
                <li><i class="fas fa-check"></i> Consistent quality across large runs</li>
              </ul>
            </div>

            <div class="applications">
              <h3>Common Applications</h3>
              <ul>
                <li>Magazines and catalogs</li>
                <li>Books and booklets</li>
                <li>Large format posters</li>
                <li>Packaging materials</li>
                <li>Corporate brochures</li>
                <li>Annual reports</li>
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
.offset-printing {
  padding-top: 80px;
}

.service-hero {
  background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://images.unsplash.com/photo-1562654435-c3c7164caa4f?w=1920&q=80');
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