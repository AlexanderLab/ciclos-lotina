<template>
  <q-page class="q-pa-md">
    <div class="row q-col-gutter-lg justify-center">
      <div class="col-12 text-center q-mb-xl">
        <h1 class="text-h2 text-weight-bold text-white">Contacto</h1>
        <p class="text-subtitle1 text-white opacity-80">¿Tienes alguna duda? Estamos aquí para ayudarte. <br> Puedes contactarnos a través de nuestro teléfono, correo electrónico o visitarnos en nuestra tienda.</p>
      </div>

      <div class="col-12 col-md-6">
        <q-card class="contact-info-card full-height">
          <q-card-section>
            <div class="text-h5 text-weight-bold q-mb-lg">Información de Contacto</div>
            
            <div class="row items-center q-mb-md">
              <q-icon name="place" size="24px" color="primary" class="q-mr-md" />
              <div>
                <div class="text-weight-bold">Dirección</div>
                <div class="text-grey-8">Astillero 12, 48013 Zorroza, Bilbao</div>
              </div>
            </div>

            <div class="row items-center q-mb-md">
              <q-icon name="phone" size="24px" color="primary" class="q-mr-md" />
              <div>
                <div class="text-weight-bold">Teléfono</div>
                <div class="text-grey-8">+34 946 547 663</div>
              </div>
            </div>

            <div class="row items-center q-mb-md">
              <q-icon name="mail" size="24px" color="primary" class="q-mr-md" />
              <div>
                <div class="text-weight-bold">Email</div>
                <div class="text-grey-8">tienda@cicloslotina.com</div>
              </div>
            </div>

            <div class="row items-center q-mb-md">
              <q-icon name="schedule" size="24px" color="primary" class="q-mr-md" />
              <div>
                <div class="text-weight-bold">Horario</div>
                <div class="text-grey-8">Lunes a Viernes: 10:00 - 13:30, 16:00 - 20:00<br>Sábados: 10:00 - 13:30</div>
              </div>
            </div>
            <div class="col-12 col-md-6">
              <q-card class="contact-info-card full-height shadow-10">
                <q-card-section class="q-pa-none overflow-hidden" style="border-radius: 12px 12px 0 0">
                  <!-- Mapa de Google Maps -->
                  <iframe
                    src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3597.0108760051276!2d-2.976081823367714!3d43.27569437676434!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd4e50614381f651%3A0xe258626a70aa96ea!2sC.%20Astillero%2C%2012%2C%20Basurto-Zorroza%2C%2048013%20Bilbao%2C%20Vizcaya!5e1!3m2!1ses!2ses!4v1769966627692!5m2!1ses!2ses"
                    width="100%" 
                    height="300" 
                    style="border:0;" 
                    allowfullscreen="" 
                    loading="lazy" 
                    referrerpolicy="no-referrer-when-downgrade">
                  </iframe>
                </q-card-section>
                <q-card-section class="q-pa-lg text-center">
                  <q-btn 
                    color="primary" 
                    outline 
                    icon="map" 
                    label="Ver en Google Maps" 
                    class="full-width"
                    href="https://maps.app.goo.gl/Guh2Zqn9NZjDJgPM6" 
                    target="_blank"
                  />
                </q-card-section>
              </q-card>
            </div>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script setup>
</script>

<style scoped lang="scss">
.constrain-width {
  max-width: 1200px;
  margin: 0 auto;
}

.contact-info-card, .contact-form-card {
  border-radius: 12px;
  background-color: rgba(255, 255, 255, 0.95);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

h1 {
  margin-top: 2rem;
  margin-bottom: 0.5rem;
}
</style>
