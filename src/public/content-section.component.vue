<template>
  <div>
    <!-- Large full-screen hero carousel -->
    <div class="carousel-container">
      <div class="carousel-wrapper">
        <div
            v-for="(concert, index) in concerts"
            :key="index"
            :class="['carousel-slide', { active: currentSlide === index }]"
        >
          <img :src="concert.image" :alt="concert.name" class="carousel-image">
          <div class="carousel-info">
            <h3>{{ $t('heroTitle') }}</h3>
            <p>{{ $t('heroSubtitle') }}</p>
          </div>
        </div>
      </div>
      <div class="carousel-dots">
        <span
            v-for="(concert, index) in concerts"
            :key="'dot-' + index"
            :class="['dot', { active: currentSlide === index }]"
            @click="goToSlide(index)"
        ></span>
      </div>
    </div>

    <!-- Decorative circles section divider -->
    <div class="section-divider">
      <div class="circle circle-1"></div>
      <div class="circle circle-2"></div>
      <div class="circle circle-3"></div>
      <div class="circle circle-4"></div>
    </div>

    <div class="section-title">{{$t("conoce")}}</div>

    <div class="concerts">
      <div class="concert-card">
        <img :src="concerts[0].image" :alt="concerts[0].name">
        <div>
          <strong>{{ concerts[0].name }}</strong><br>
          {{ concerts[0].date }}, {{ concerts[0].venue }}
        </div>
      </div>

      <div class="concert-card">
        <img :src="concerts[1].image" :alt="concerts[1].name">
        <div>
          <strong>{{ concerts[1].name }}</strong><br>
          {{ concerts[1].date }}, {{ concerts[1].venue }}
        </div>
      </div>

      <div class="concert-card">
        <img :src="concerts[2].image" :alt="concerts[2].name">
        <div>
          <strong>{{ concerts[2].name }}</strong><br>
          {{ concerts[2].date }}, {{ concerts[2].venue }}
        </div>
      </div>

      <div class="concert-card">
        <img :src="concerts[3].image" :alt="concerts[3].name">
        <div>
          <strong>{{ concerts[3].name }}</strong><br>
          {{ concerts[3].date }}, {{ concerts[3].venue }}
        </div>
      </div>

      <div class="concert-card">
        <img :src="concerts[4].image" :alt="concerts[4].name">
        <div>
          <strong>{{ concerts[4].name }}</strong><br>
          {{ concerts[4].date }}, {{ concerts[4].venue }}
        </div>
      </div>
      <div class="concert-card">
        <img :src="concerts[5].image" :alt="concerts[5].name">
        <div>
          <strong>{{ concerts[5].name }}</strong><br>
          {{ concerts[5].date }}, {{ concerts[5].venue }}
        </div>
      </div>
    </div>

    <div class="section-divider">
      <div class="circle circle-1"></div>
      <div class="circle circle-2"></div>
      <div class="circle circle-3"></div>
      <div class="circle circle-4"></div>
    </div>

    <div class="testimonial-title">{{$t("Testimonios")}}</div>

    <div class="testimonials-container">
      <div class="testimonial-card">
        <img src="https://raw.githubusercontent.com/The-Rumbling-AW/LandingV2/refs/heads/main/stay.jpg" alt="Fan de Stray Kids">
        <p>
          {{$t("testuno")}}<br><br>
          {{$t("testunoby")}}
        </p>
      </div>

      <div class="testimonial-card highlighted">
        <img src="https://raw.githubusercontent.com/The-Rumbling-AW/LandingV2/refs/heads/main/harry.jpg" alt="Fan de Harry Styles">
        <p>
          {{$t("testdos")}}<br><br>
          {{$t("testdosby")}}
        </p>
      </div>

      <div class="testimonial-card">
        <img src="https://raw.githubusercontent.com/The-Rumbling-AW/LandingV2/refs/heads/main/louis.jpg" alt="Fan de Louis Tomlinson">
        <p>
          {{$t("testtres")}}<br><br>
          {{$t("testtresby")}}
        </p>
      </div>
    </div>

    <div class="section-divider">
      <div class="circle circle-1"></div>
      <div class="circle circle-2"></div>
      <div class="circle circle-3"></div>
      <div class="circle circle-4"></div>
    </div>

    <div class="testimonial-title">{{$t("abouttheteam")}}</div>
    <div class="video-section video-left">
      <div class="video-media">
        <iframe
            src="https://www.youtube.com/embed/Fa3EgjYHyow"
            title="About The Team"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            allowfullscreen>
        </iframe>
      </div>
      <div class="video-content">

        <p>{{$t("abouttheteamdesc")}}</p>
      </div>
    </div>

    <div class="section-divider">
      <div class="circle circle-1"></div>
      <div class="circle circle-2"></div>
      <div class="circle circle-3"></div>
      <div class="circle circle-4"></div>
    </div>

    <div class="testimonial-title">{{$t("abouttheproduct")}}</div>
    <div class="video-section video-right">
      <div class="video-content">

        <p>{{$t("abouttheproductdesc")}}</p>
      </div>
      <div class="video-media">
        <iframe
            src="https://www.youtube.com/embed/Fa3EgjYHyow"

            title="About The Product"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            allowfullscreen>
        </iframe>
      </div>
    </div>

    <!-- Added purple email signup section before footer -->
    <div class="email-signup-section">
      <div class="signup-circles">
        <div class="circle circle-1"></div>
        <div class="circle circle-2"></div>
        <div class="circle circle-3"></div>
        <div class="circle circle-4"></div>
      </div>
      <div class="email-signup-content">
        <h2>{{ $t('footer') }}</h2>
        <p>{{ $t('footerdos') }}</p>
        <form class="signup-form" @submit.prevent>
          <input type="email" :placeholder="$t('footercorreo')" required />
          <button type="submit">{{ $t('footerboton') }}</button>
        </form>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "content-section",
  data() {
    return {
      currentSlide: 0,
      concerts: [
        {
          name: "Maldito Antisocial",
          date: "17 de Octubre 2025",
          venue: "Explanada Agua Dulce",
          image: "https://cdn.myportfolio.com/652b25c3-c66e-4abb-a7c1-36ca2ad2ad92/e4dc6579-20de-40ed-88c0-9816e26304df_rw_1920.jpg?h=29697d3c2c0b321ee7007ceae245effd"
        },
        {
          name: "Big Time Rush",
          date: "27 de Febrero 2026",
          venue: "Costa 21",
          image: "https://www.sportovnihalafortuna.cz/data/a/a/btr-1920x600-002-.jpg"
        },
        {
          name: "Cometa a la deriva",
          date: "11 de Octubre 2025",
          venue: "Parque Washington",
          image: "https://tercerparlante.com/wp-content/uploads/2025/01/Cometa-a-la-Deriva-Peru-2025-0001.jpg"
        },
        {
          name: "Dua Lipa",
          date: "25 de Noviembre 2025",
          venue: "Estadio San Marcos",
          image: "https://images.hdqwalls.com/wallpapers/2019-dua-lipa-c0.jpg"
        },
        {
          name: "Bad Bunny",
          date: "30 de Enero 2025",
          venue: "Estadio Nacional",
          image: "https://media.pitchfork.com/photos/682b43f9d6a2575d172e91a4/16:9/w_1280,c_limit/Bad-Bunny-Debi-Tirar-Mas-Fotos.jpeg"
        },
        {
          name: "Doja Cat",
          date: "13 de Febrero 2026",
          venue: "Arena 1",
          image: "https://4kwallpapers.com/images/wallpapers/doja-cat-american-3840x2160-9919.jpg"
        }
      ],
      intervalId: null
    }
  },
  mounted() {
    this.startCarousel();
  },
  beforeUnmount() {
    this.stopCarousel();
  },
  methods: {
    startCarousel() {
      this.intervalId = setInterval(() => {
        this.nextSlide();
      }, 5000);
    },
    stopCarousel() {
      if (this.intervalId) {
        clearInterval(this.intervalId);
      }
    },
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.concerts.length;
    },
    goToSlide(index) {
      this.currentSlide = index;
      this.stopCarousel();
      this.startCarousel();
    }
  }
}
</script>

<style scoped>
/* Component-specific styles are in the main style.css */
</style>
