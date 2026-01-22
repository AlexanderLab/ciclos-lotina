<template>
  <q-page class="q-pa-md">
    <div class="row q-col-gutter-lg justify-center">
      <div class="col-12 text-center q-mb-xl">
        <h1 class="text-h2 text-weight-bold text-white">Nuestros Servicios</h1>
        <p class="text-subtitle1 text-white opacity-80">Para unos es profesión, para mí es pasión. <br> Si quieres que traten a tu bici como lo harías tú, este es tu lugar. <br> El taller que cuida de cada bici como si fuera única.<br> Somos pequeños en superficie pero grandes en soluciones.</p>
      </div>

      <div 
        v-for="(service, index) in SERVICES" 
        :key="index"
        class="col-12 col-sm-6 col-md-4"
      >
        <q-card 
          class="service-card full-height cursor-pointer"
          @click="openDetail(service)"
        >
          <q-card-section class="text-center">
            <q-icon :name="service.icon" size="64px" color="primary" class="q-mb-md" />
            <div class="text-h5 text-weight-bold q-mb-sm text-primary">{{ service.title }}</div>
            <p class="text-body1 text-grey-8">{{ service.description }}</p>
            <q-img
              :src="service.images[0]"
              :ratio="16/9"
              fit="cover"
              class="brand-image shadow-10 q-mt-md"
            />
          </q-card-section>
          
          <q-card-actions align="center" class="q-pb-md">
            <q-btn flat color="primary" label="Ver más" />
          </q-card-actions>
        </q-card>
      </div>
    </div>

    <!-- Detail Dialog -->
    <q-dialog v-model="dialogVisible" backdrop-filter="blur(4px)">
      <q-card style="width: 700px; max-width: 90vw; border-radius: 16px;">
        <div class="relative-position">
          <q-carousel
            v-model="slide"
            swipeable
            animated
            arrows
            navigation
            infinite
            :ratio="21/9"
            class="service-carousel cursor-pointer"
            @click="nextSlide"
          >
            <q-carousel-slide 
              v-for="(img, idx) in selectedService.images" 
              :key="idx" 
              :name="idx" 
              :img-src="img" 
            />
            
            <template v-slot:control>
              <q-carousel-control
                position="top-right"
                :offset="[18, 18]"
              >
                <q-btn 
                  icon="close" 
                  flat 
                  round 
                  dense 
                  v-close-popup 
                  class="text-white bg-black-opacity"
                />
              </q-carousel-control>
            </template>
          </q-carousel>
          <div class="absolute-bottom text-h5 text-weight-bold q-pa-md bg-gradient-dark text-white">
            {{ selectedService.title }}
          </div>
        </div>

        <q-card-section class="q-pa-lg">
          <div class="row items-center q-mb-md">
            <q-icon :name="selectedService.icon" size="32px" color="primary" class="q-mr-md" />
            <div class="text-h6 text-primary">{{selectedService.subtitle}}</div>
          </div>
          
          <p class="text-body1 text-grey-9 line-height-relaxed">
            {{ selectedService.details }}
          </p>

          <div class="q-mt-xl row justify-end">
            <q-btn unelevated color="primary" label="Cerrar" v-close-popup class="q-px-lg" />
          </div>
        </q-card-section>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const dialogVisible = ref(false)
const selectedService = ref({ images: [] })
const slide = ref(0)

const nextSlide = () => {
  if (selectedService.value.images?.length > 0) {
    slide.value = (slide.value + 1) % selectedService.value.images.length
  }
}

const SERVICES = [
  {
    title: 'Taller Especializado',
    subtitle: 'Nuestra pasión, las bicis',
    icon: 'pedal_bike',
    description: 'Reparación y mantenimiento integral de todo tipo de bicicletas: montaña, carretera, urbanas y eléctricas.',
    images: ['/virgi_trabajando.jpeg'],
    details: 'Nuestro taller cuenta con herramientas de precisión y personal altamente cualificado. Realizamos desde ajustes básicos hasta reconstrucciones completas, servicio de suspensiones, purgado de frenos hidráulicos etc... Cada bicicleta es tratada con el máximo cuidado y atención al detalle, garantizando que vuelvas a la ruta con total seguridad.'
  },
  {
    title: 'Venta de Bicicletas',
    subtitle: 'Tu próxima aventura empieza aquí',
    icon: 'shopping_basket',
    description: 'Disponemos de una amplia gama de bicicletas de las mejores marcas, adaptadas a todos los niveles y necesidades.',
    images: ['/bici1.jpeg', '/bici2.jpeg', '/bici3.jpeg', '/bici4.jpeg', '/bici5.jpeg'],
    details: 'Te asesoramos de forma personalizada para que encuentres la bicicleta perfecta para tu estilo de vida. Contamos con modelos de carretera, montaña, gravel y una excelente selección de bicicletas de última generación. Todas nuestras bicicletas se entregan totalmente ajustadas y con un servicio de postventa excepcional.'
  },
  {
    title: 'Accesorios y Componentes',
    subtitle: 'Todo lo que tu bici y tú necesitáis',
    icon: 'settings',
    description: 'Equípate con lo mejor: cascos, zapatillas, ropa técnica y componentes de alta calidad para mejorar tu rendimiento.',
    images: ['/foto4.jpeg', '/foto2.jpeg', '/foto3.jpeg'],
    details: 'La seguridad y el rendimiento son nuestra priority. Trabajamos con marcas líderes en el sector para ofrecerte equipamiento de alta calidad: cascos con tecnología MIPS, calzado ergonómico, ropa técnica transpirable y componentes de transmisión de alto nivel. Si buscas mejorar tu experiencia sobre la bici, aquí encontrarás los mejores componentes.'
  }
]

const openDetail = (service) => {
  selectedService.value = service
  slide.value = 0
  dialogVisible.value = true
}
</script>

<style scoped lang="scss">
.constrain-width {
  max-width: 1200px;
  margin: 0 auto;
}

.service-card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  border-radius: 12px;
  overflow: hidden;
  background-color: rgba(255, 255, 255, 0.95);
  border: 1px solid rgba(255, 255, 255, 0.2);

  &:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
    background-color: rgba(255, 255, 255, 1);
  }
}

.brand-image {
  border-radius: 12px;
  border: 4px solid white;
  width: 100%;
}

h1 {
  margin-top: 2rem;
  margin-bottom: 0.5rem;
}

.bg-gradient-dark {
  background: linear-gradient(transparent, rgba(0, 0, 0, 0.8));
}

.bg-black-opacity {
  background: rgba(0, 0, 0, 0.3);
}

.line-height-relaxed {
  line-height: 1.6;
}
</style>

