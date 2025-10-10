<script>
export default {
  name: "artist-section.component"
}
</script>

<template>
  <main>
    <h2>
      {{ $t('titulo_beneficios_artista_parte1') }}
      <span class="highlight">{{ $t('titulo_beneficios_artista_resaltado') }}</span>
      {{ $t('titulo_beneficios_artista_parte2') }}
    </h2>

    Added decorative circles section divider
    <div class="section-divider">
      <div class="circle circle-1"></div>
      <div class="circle circle-2"></div>
      <div class="circle circle-3"></div>
      <div class="circle circle-4"></div>
    </div>

    <section class="benefits">
      <div class="card">
        <div class="icon"><i class="fas fa-bell"></i></div>
        <p>
          {{ $t('beneficioartista1_parte1') }}
          <span class="highlight">{{ $t('beneficioartista1_resaltado') }}</span>,
          {{ $t('beneficioartista1_parte2') }}
        </p>
      </div>

      <div class="card red">
        <div class="icon"><i class="fas fa-envelope"></i></div>
        <p>
          {{ $t('beneficioartista2_parte1') }}<br/>
          {{ $t('beneficioartista2_parte2') }}
        </p>
      </div>

      <div class="card">
        <div class="icon"><i class="fas fa-user-friends"></i></div>
        <p>
          {{ $t('beneficioartista3_parte1') }}<br/>
          <span class="highlight">{{ $t('beneficioartista3_resaltado') }}</span>
          {{ $t('beneficioartista3_parte2') }}
        </p>
      </div>

      <div class="card red">
        <div class="icon"><i class="fas fa-map"></i></div>
        <p>
          {{ $t('beneficioartista4_parte1') }}<br/>
          {{ $t('beneficioartista4_parte2') }}
        </p>
      </div>
    </section>
  </main>
</template>

<style scoped>
main {
  text-align: center;
  padding: 2rem 1rem;
}

/* Updated highlight color to new brand red */
.highlight {
  color: #8C1C25;
}

.benefits {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
  margin-top: 2rem;
}
/* Card */

.card {
  background-color: #fff;
  color: #000;
  padding: 2rem 1rem;
  width: 230px;
  min-height: 280px;
  border-radius: 30px;
  text-align: left;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  justify-content: flex-start;
  align-items: flex-start;
  font-size: 1.5rem;
  line-height: 1.6;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 20px rgba(140, 28, 37, 0.5);
}

.card .icon {
  font-size: 2rem;
  align-self: center;
  margin-bottom: 1rem;
}

nav a.active {
  color: #8C1C25;
  font-weight: bold;
}

/* Updated card color from purple to red */
.card.red {
  background-color: #8C1C25;
  color: #fff;
}
/* Link */

.link {
  margin-top: 2rem;
}

.link a {
  color: #8C1C25;
  text-decoration: none;
}
</style>
