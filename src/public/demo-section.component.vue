<template>
  <div class="demo-section">
    <div class="demo-container">
        <div class="demo-header">
          <h1>{{ $t('demoTitle') }}</h1>
          <p>{{ $t('demoSubtitle') }}</p>
        </div>

        <!-- Decorative circles section divider -->
        <div class="section-divider">
          <div class="circle circle-1"></div>
          <div class="circle circle-2"></div>
          <div class="circle circle-3"></div>
          <div class="circle circle-4"></div>
        </div>

        <div class="carousel-container">
          <div class="carousel-wrapper">
            <!-- Show only 3 items at a time with proper positioning -->
            <div
              v-for="n in 3"
              :key="'visible-' + n"
              class="carousel-item"
              :class="getItemClass(n - 2)"
              :style="getItemStyle(n - 2)"
            >
              <img :src="getCurrentMockup(n - 2).image" :alt="getCurrentMockup(n - 2).title" />
              <div class="mockup-info">
                <h3>{{ getCurrentMockup(n - 2).title }}</h3>
                <p>{{ getCurrentMockup(n - 2).description }}</p>
              </div>
            </div>
          </div>

          <div class="carousel-indicators">
            <button
              v-for="(mockup, index) in mockups"
              :key="'indicator-' + index"
              class="indicator"
              :class="{ active: index === currentIndex }"
              @click="goToSlide(index)"
            ></button>
          </div>

          <button class="nav-btn prev" @click="prevSlide">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <polyline points="15,18 9,12 15,6"></polyline>
            </svg>
          </button>

          <button class="nav-btn next" @click="nextSlide">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <polyline points="9,18 15,12 9,6"></polyline>
            </svg>
          </button>
        </div>

        <!-- Decorative circles section divider -->
        <div class="section-divider">
          <div class="circle circle-1"></div>
          <div class="circle circle-2"></div>
          <div class="circle circle-3"></div>
          <div class="circle circle-4"></div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: "DemoSection",
  components: {},
  data() {
    return {
      currentIndex: 0,
      autoPlayInterval: null,
      mockups: [
        {
          title: "Inicio",
          description: "Pantalla de bienvenida",
          image: "/LandingPage-GigMap-V1/mockup-inicio.png"
        },
        {
          title: "Iniciar Sesión",
          description: "Acceso a tu cuenta",
          image: "/LandingPage-GigMap-V1/mockup-login.png"
        },
        {
          title: "Registro",
          description: "Crear nueva cuenta",
          image: "/LandingPage-GigMap-V1/mockup-registro.png"
        },
        {
          title: "Home",
          description: "Comunidades y conciertos cercanos",
          image: "/LandingPage-GigMap-V1/mockup-home.png"
        },
        {
          title: "Descubrir Conciertos",
          description: "Explora eventos disponibles",
          image: "/LandingPage-GigMap-V1/mockup-descubrir.png"
        },
        {
          title: "Filtros",
          description: "Busca por género, fecha y ubicación",
          image: "/LandingPage-GigMap-V1/mockup-filtros.png"
        },
        {
          title: "Mapa Interactivo",
          description: "Localiza eventos en tiempo real",
          image: "/LandingPage-GigMap-V1/mockup-mapa.png"
        },
        {
          title: "Comunidades",
          description: "Únete a grupos musicales",
          image: "/LandingPage-GigMap-V1/mockup-comunidades.png"
        },
        {
          title: "Comunidad Específica",
          description: "Vista detallada de una comunidad",
          image: "/LandingPage-GigMap-V1/mockup-comunidad.png"
        },
        {
          title: "Perfil",
          description: "Tu información personal",
          image: "/LandingPage-GigMap-V1/mockup-perfil.png"
        },
        {
          title: "Editar Perfil",
          description: "Modifica tu información personal",
          image: "/LandingPage-GigMap-V1/mockup-edit.png"
        }
      ]
    };
  },
  mounted() {
    this.startAutoPlay();
  },
  beforeUnmount() {
    this.stopAutoPlay();
  },
  methods: {
    startAutoPlay() {
      this.autoPlayInterval = setInterval(() => {
        this.nextSlide();
      }, 4000);
    },
    stopAutoPlay() {
      if (this.autoPlayInterval) {
        clearInterval(this.autoPlayInterval);
        this.autoPlayInterval = null;
      }
    },
    getCurrentMockup(offset) {
      const total = this.mockups.length;
      const index = (this.currentIndex + offset + total) % total;
      return this.mockups[index];
    },
    getItemClass(offset) {
      if (offset === 0) return 'center';
      return offset < 0 ? 'left' : 'right';
    },
    getItemStyle(offset) {
      let scale = 0.85;
      let opacity = 0.6;
      let zIndex = 1;
      let blur = 'blur(2px)';
      let brightness = 'brightness(0.7)';

      if (offset === 0) {
        scale = 1;
        opacity = 1;
        zIndex = 3;
        blur = 'blur(0px)';
        brightness = 'brightness(1)';
      } else if (Math.abs(offset) === 1) {
        scale = 0.95;
        opacity = 0.8;
        zIndex = 2;
        blur = 'blur(1px)';
        brightness = 'brightness(0.85)';
      }

      return {
        transform: `scale(${scale})`,
        opacity: opacity,
        zIndex: zIndex,
        filter: `${blur} ${brightness}`,
        transition: 'all 0.8s cubic-bezier(0.4, 0, 0.2, 1)'
      };
    },
    nextSlide() {
      this.currentIndex = (this.currentIndex + 1) % this.mockups.length;
    },
    prevSlide() {
      this.currentIndex = this.currentIndex === 0 ? this.mockups.length - 1 : this.currentIndex - 1;
    },
    goToSlide(index) {
      this.currentIndex = index;
    }
  }
}
</script>

<style scoped>
.demo-section {
  min-height: calc(100vh - 160px);
  background: linear-gradient(135deg, #000 0%, #1a1a1a 100%);
  padding: 8rem 2rem 4rem;
  color: #fff;
}

.demo-container {
  max-width: 1200px;
  margin: 0 auto;
}

.demo-header {
  text-align: center;
  margin-bottom: 3rem;
}

.demo-header h1 {
  font-size: 3rem;
  font-weight: 800;
  margin-bottom: 1rem;
  background: #8c1c25;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.demo-header p {
  font-size: 1.2rem;
  color: #ccc;
  max-width: 600px;
  margin: 0 auto;
}

/* Decorative circles with new colors */
.section-divider {
  position: relative;
  height: 120px;
  overflow: hidden;
}

.section-divider .circle {
  position: absolute;
  border-radius: 50%;
  opacity: 0.5;
  animation: float-gently 6s ease-in-out infinite;
}

.section-divider .circle-1 {
  background-color: #590e0e;
  width: 80px;
  height: 80px;
  left: 15%;
  top: 20px;
  animation-delay: 0s;
}

.section-divider .circle-2 {
  background-color: #8c1c25;
  width: 50px;
  height: 50px;
  left: 35%;
  top: 50px;
  animation-delay: 1.5s;
}

.section-divider .circle-3 {
  background-color: rgba(255, 255, 255, 0.3);
  width: 60px;
  height: 60px;
  right: 35%;
  top: 15px;
  animation-delay: 3s;
  animation: float-sideways 5s ease-in-out infinite;
}

.section-divider .circle-4 {
  background-color: #590e0e;
  width: 90px;
  height: 90px;
  right: 12%;
  top: 35px;
  animation-delay: 4.5s;
}

.carousel-container {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  overflow: hidden;
}

.carousel-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 2rem;
  min-height: 700px;
}

.carousel-item {
  flex: 0 0 280px;
  transition: all 1.2s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  position: relative;
  cursor: pointer;
}

.carousel-item.center {
  flex: 0 0 320px;
}

.carousel-item img {
  width: 100%;
  height: 650px;
  object-fit: contain;
  border-radius: 20px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
  transition: all 1.2s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.carousel-item.center img {
  box-shadow: 0 30px 80px rgba(140, 28, 37, 0.4);
}

.carousel-item:hover img {
  transform: translateY(-5px);
}

.mockup-info {
  position: absolute;
  bottom: 2rem;
  left: 2rem;
  right: 2rem;
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(10px);
  padding: 1.5rem;
  border-radius: 15px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.mockup-info h3 {
  margin: 0 0 0.5rem 0;
  font-size: 1.5rem;
  font-weight: 700;
  color: #fff;
}

.mockup-info p {
  margin: 0;
  color: #ccc;
  font-size: 1rem;
  line-height: 1.4;
}

.carousel-indicators {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-top: 3rem;
}

.indicator {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  border: 2px solid rgba(255, 255, 255, 0.3);
  background: transparent;
  cursor: pointer;
  transition: all 0.3s ease;
}

.indicator:hover {
  background: rgba(255, 255, 255, 0.5);
}

.indicator.active {
  background: #8c1c25;
  border-color: #8c1c25;
  box-shadow: 0 0 20px rgba(140, 28, 37, 0.6);
}

.nav-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  color: #fff;
}

.nav-btn:hover {
  background: rgba(140, 28, 37, 0.8);
  border-color: #8c1c25;
  transform: translateY(-50%) scale(1.1);
}

.nav-btn.prev {
  left: 2rem;
}

.nav-btn.next {
  right: 2rem;
}

.nav-btn svg {
  width: 24px;
  height: 24px;
}

@media (max-width: 768px) {
  .demo-header h1 {
    font-size: 2rem;
  }

  .carousel-item {
    flex: 0 0 220px;
    margin: 0 8px;
  }

  .carousel-item.center {
    flex: 0 0 260px;
  }

  .carousel-item img {
    height: 500px;
  }

  .nav-btn {
    width: 50px;
    height: 50px;
  }

  .nav-btn.prev {
    left: 1rem;
  }

  .nav-btn.next {
    right: 1rem;
  }
}
</style>
