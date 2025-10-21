<template>
  <div class="download-section">
    <div class="download-container">
        <div class="download-header">
          <h1>{{ $t('descargarApp') }}</h1>
          <p>{{ $t('eligePlataforma') }}</p>
        </div>

        <!-- Decorative circles section divider -->
        <div class="section-divider">
          <div class="circle circle-1"></div>
          <div class="circle circle-2"></div>
          <div class="circle circle-3"></div>
          <div class="circle circle-4"></div>
        </div>

        <div class="platform-options">
          <div class="platform-card apple-card" @click="downloadApple">
            <div class="platform-image">
              <img src="/LandingPage-GigMap-V1/apple-logo.png" alt="iOS App" />
            </div>
            <div class="platform-info">
              <h2>iOS</h2>
              <p>{{ $t('proximamente') }}</p>
            </div>
          </div>

          <div class="platform-card android-card" @click="downloadAndroid">
            <div class="platform-image">
              <img src="/LandingPage-GigMap-V1/android-logo.png" alt="Android App" />
            </div>
            <div class="platform-info">
              <h2>Android</h2>
              <p>{{ $t('descargarAhora') }}</p>
            </div>
          </div>
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
  name: "DownloadPage",
  components: {},
  methods: {
    downloadApple() {
      alert('Próximamente disponible para iOS');
    },
    downloadAndroid() {
      const link = document.createElement('a');
      link.href = 'https://github.com/StayBits/GigMap-mobile/releases/download/v1.0.0/app-debug.apk';
      link.download = 'GigMap.apk';
      link.target = '_blank';
      link.rel = 'noopener';
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    }
  }
}
</script>

<style scoped>
.download-section {
  min-height: calc(100vh - 160px);
  background: linear-gradient(135deg, #000 0%, #1a1a1a 100%);
  padding: 8rem 2rem 4rem;
  color: #fff;
}

.download-container {
  max-width: 800px;
  margin: 0 auto;
}

.download-header {
  text-align: center;
  margin-bottom: 3rem;
}

.download-header h1 {
  font-size: 3rem;
  font-weight: 800;
  margin-bottom: 1rem;
  background: #8c1c25;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.download-header p {
  font-size: 1.3rem;
  color: #ccc;
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

.platform-options {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 3rem;
  max-width: 1000px;
  margin: 0 auto 3rem;
}

.platform-card {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 3rem 2rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  min-height: 350px;
}

.platform-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.apple-card:hover {
  border-color: #007AFF;
  background: rgba(0, 122, 255, 0.1);
}

.android-card:hover {
  border-color: #8c1c25;
  background: rgba(140, 28, 37, 0.1);
}

.platform-image {
  margin-bottom: 1.5rem;
}

.platform-image img {
  width: 120px;
  height: 120px;
  object-fit: contain;
}

.platform-info h2 {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 1rem;
  color: #fff;
}

.platform-info p {
  color: #ccc;
  margin: 0;
  font-size: 1.2rem;
  line-height: 1.4;
}

@media (max-width: 768px) {
  .download-section {
    padding: 2rem 1rem 1rem;
  }

  .download-header h1 {
    font-size: 2rem;
  }

  .platform-options {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .platform-card {
    padding: 2rem 1.5rem;
    min-height: 300px;
  }

  .platform-image img {
    width: 100px;
    height: 100px;
  }

  .platform-info h2 {
    font-size: 1.5rem;
  }
}
</style>
