<template>
  <q-layout view="lHh Lpr lff">
    <q-header elevated class="bg-primary">
      <q-toolbar class="constrain-width">
        <!-- Logo/Title -->
        <q-toolbar-title class="logo-container" shrink>
          <router-link to="/" class="title-link">
            <q-img src="/logo.jpeg" class="header-logo" fit="contain" />
          </router-link>
        </q-toolbar-title>

        <q-space />

        <!-- Desktop Navigation -->
        <div class="desktop-nav gt-sm">
          <q-btn flat label="Inicio" to="/" :class="{ 'active-nav': currentTab === 'home' }" />
          <q-btn flat label="Servicios" to="/servicios" :class="{ 'active-nav': currentTab === 'servicios' }" />
          <q-btn flat label="Contacto" to="/contacto" :class="{ 'active-nav': currentTab === 'contacto' }" />
        </div>

        <!-- Mobile Menu Button -->
        <q-btn
          flat
          dense
          round
          icon="menu"
          class="lt-md q-ml-sm text-white"
          @click="toggleDrawer"
        />
      </q-toolbar>
    </q-header>

    <!-- Mobile Drawer -->
    <q-drawer v-model="drawerOpen" side="right" overlay behavior="mobile" class="bg-primary">
      <q-list dark>
        <q-item-label header class="text-white">CICLOS LOTINA</q-item-label>
        
        <q-item clickable v-ripple to="/" @click="drawerOpen = false" active-class="text-white bg-white-transparent">
          <q-item-section avatar><q-icon name="home" /></q-item-section>
          <q-item-section>Inicio</q-item-section>
        </q-item>

        <q-item clickable v-ripple to="/servicios" @click="drawerOpen = false" active-class="text-white bg-white-transparent">
          
          <q-item-section avatar><q-icon name="pedal_bike" /></q-item-section>
          <q-item-section>Servicios</q-item-section>
        </q-item>

        <q-item clickable v-ripple to="/contacto" @click="drawerOpen = false" active-class="text-white bg-white-transparent">
          <q-item-section avatar><q-icon name="contact_mail" /></q-item-section>
          <q-item-section>Contacto</q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-primary q-pa-md">
      <div class="footer-content constrain-width text-center">
        <div class="text-white text-caption">
          © {{ new Date().getFullYear() }} Ciclos Lotina.
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>

<script setup>
import { ref, watch } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();
const currentTab = ref('home');
const drawerOpen = ref(false);

watch(() => route.path, (newPath) => {
  if (newPath === '/' || newPath === '') currentTab.value = 'home';
  else if (newPath.startsWith('/servicios')) currentTab.value = 'servicios';
  else if (newPath.startsWith('/contacto')) currentTab.value = 'contacto';
}, { immediate: true });

function toggleDrawer() {
  drawerOpen.value = !drawerOpen.value;
}
</script>

<style scoped lang="scss">
.constrain-width {
  max-width: 1400px;
  margin: 0 auto;
  width: 100%;
}

.q-toolbar.constrain-width {
  min-height: 70px;
}

.text-primary {
  color: $primary !important;
}

.title-link {
  text-decoration: none;
  display: flex;
  align-items: center;
  
  span {
    font-weight: 700;
  }
}

.logo-container {
  display: flex;
  align-items: center;
  padding: 5px 0;
}

.header-logo {
  width: 200px;
  height: 80px;
  transition: all 0.3s ease;

  @media (max-width: 599px) { // xs breakpoint
    width: 150px;
    height: 60px;
  }
}

.desktop-nav {
  display: flex;
  gap: 1rem;

  :deep(.q-btn) {
    color: white;
    opacity: 0.85;
    font-weight: 600;

    &:hover {
      opacity: 1;
      background-color: rgba($primary, 0.05);
    }

    &.active-nav {
      opacity: 1;
      border-bottom: 2px solid $primary;
      border-radius: 0;
    }
  }
}

.bg-white-transparent {
  background-color: rgba(255, 255, 255, 0.1);
}
</style>
