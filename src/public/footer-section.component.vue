<template>

  <footer>
    <div class="footer-container">
      <div class="footer-columns">
        <div class="footer-column">
          <h4>{{ $t('paraFans') }}</h4>
          <ul>
            <li><a href="#">{{ $t('buscarEventos') }}</a></li>
            <li><a href="#">{{ $t('crearCuenta') }}</a></li>
            <li><a href="#">{{ $t('ayuda') }}</a></li>
          </ul>
        </div>

        <div class="footer-column">
          <h4>{{ $t('paraArtistas') }}</h4>
          <ul>
            <li><a href="#">{{ $t('registrarEvento') }}</a></li>
            <li><a href="#">{{ $t('herramientas') }}</a></li>
            <li><a href="#">{{ $t('recursos') }}</a></li>
          </ul>
        </div>

        <div class="footer-column">
          <h4>{{ $t('empresa') }}</h4>
          <ul>
            <li><a href="#">{{ $t('sobreNosotros') }}</a></li>
            <li><a href="#">{{ $t('contacto') }}</a></li>
            <li><a href="#">{{ $t('carreras') }}</a></li>
          </ul>
        </div>

        <div class="footer-column">
          <h4>{{ $t('legal') }}</h4>
          <ul>
            <li><a href="#">{{ $t('privacidad') }}</a></li>
            <li><a href="#">{{ $t('terminos') }}</a></li>
            <li><a href="#">{{ $t('cookies') }}</a></li>
          </ul>
        </div> 
      </div>

      <div class="footer-bottom">
        <p>{{ $t('copyright') }}</p>
        <div class="footer-social">
          <a href="https://www.tiktok.com" target="_blank">
            <img src="https://img.icons8.com/ios-filled/50/ffffff/tiktok--v1.png" alt="TikTok" />
          </a>
          <a href="https://twitter.com" target="_blank">
            <img src="https://img.icons8.com/ios-filled/50/ffffff/twitterx--v1.png" alt="X" />
          </a>
          <a href="https://facebook.com" target="_blank">
            <img src="https://img.icons8.com/ios-filled/50/ffffff/facebook-new.png" alt="Facebook" />
          </a>
          <a href="https://youtube.com" target="_blank">
            <img src="https://img.icons8.com/ios-filled/50/ffffff/youtube-play.png" alt="YouTube" />
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default { 
  name: "footer-section"
}
</script>

<style scoped>
/* Footer styles are now in main style.css */
</style>
