<template>
  <q-page class="flex flex-center index-page-bg">
    <div class="hero-section text-center q-pa-xl">
      <div class="logo-container q-mb-xl animate-pop">
        <q-img src="/logo.png" class="hero-logo" fit="contain" />
      </div>
      <p class="text-h5 text-white q-mb-xl opacity-80">Tu tienda de confianza para el mundo del ciclismo en Bilbao</p>
      
      <div class="row justify-center q-gutter-md">
        <q-btn label="Ver Servicios" color="white" text-color="primary" size="lg" to="/servicios" unelevated />
        <q-btn label="Contactar" outline color="white" size="lg" to="/contacto" />
      </div>
    </div>
  </q-page>
</template>

<script setup>
//
</script>

<style scoped lang="scss">
.index-page-bg {
  background-image: 
    linear-gradient(135deg, rgba(255, 193, 7, 0.05) 0%, rgba(10, 10, 10, 0.95) 100%),
    url('/entrada.jpeg');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
}

.hero-section {
  max-width: 800px;
  width: 100%;
}

.hero-logo {
  width: 600px;
  max-width: 90vw;
  height: auto;
  margin-bottom: 2rem;
  transition: all 0.3s ease;

  @media (max-width: 599px) { // xs breakpoint
    width: 280px;
  }
}

.brand-image {
  border-radius: 12px;
  border: 4px solid white;
}

.opacity-80 {
  opacity: 0.8;
}

.animate-pop {
  animation: pop 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

@keyframes pop {
  0% { transform: scale(0.5); opacity: 0; }
  100% { transform: scale(1); opacity: 1; }
}

h1 {
  letter-spacing: -2px;
  line-height: 1;
}
</style>
