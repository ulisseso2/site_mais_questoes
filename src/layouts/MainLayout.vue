<template>
  <q-layout view="hHh Lpr lff">
    <q-header elevated>
      <q-toolbar style="height: 70px" class="bg-secondary">
        <q-toolbar-title class="q-ml-md">
          <div
            class="logo"
            :style="{ backgroundImage: `url(${logoWhite})` }"
          ></div>
        </q-toolbar-title>
        <div v-if="$q.screen.gt.xs">
          <q-btn
            v-for="(page, p) in pages"
            :key="p"
            :label="page.name"
            flat
            @click="$router.push(page.path)"
          ></q-btn>
        </div>
        <q-btn
          v-if="$q.screen.xs"
          icon="menu"
          flat
          round
          dense
          @click="toggleLeftDrawer()"
        ></q-btn>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="rightDrawer"
      side="right"
      :width="300"
      :breakpoint="700"
      elevated
      overlay
      class="bg-grey-9 text-white"
    >
      <q-scroll-area class="fit">
        <q-list>
          <q-item
            v-for="(page, p) in pages"
            :key="p"
            clickable
            v-ripple
            @click="$router.push(page.path)"
          >
            <q-item-section avatar>
              <q-icon :name="page.icon"></q-icon>
            </q-item-section>
            <q-item-section>
              {{ page.name }}
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>
    <q-footer reveal elevated class="bg-secondary text-white">
      <div class="row justify-evenly items-center">
        <div>
          <q-btn
            color="secondary"
            label="maisquestoes.com.br"
            icon="home"
            @click="$router.push('/')"
          />
          <q-btn
            color="secondary"
            label="TUTORIAL"
            icon="menu_book"
            @click="$router.push('/tutorial')"
          />
        </div>
        <div class="q-pt-md">
          <p class="text-subtitle1">
            Feito com
            <span class="text-primary text-subtitle1">&#9829;</span> Mais
            Questões 2022
          </p>
        </div>
      </div>
    </q-footer>
    <q-page-container>
      <router-view />
    </q-page-container>
    <button-whatsapp />
  </q-layout>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import logoWhite from '/images/logo-white.png';
import ButtonWhatsapp from '../components/ButtonWhatsapp.vue';

export default defineComponent({
  name: 'MainLayout',

  components: { ButtonWhatsapp },

  setup() {
    const rightDrawer = ref(false);
    return {
      logoWhite,
      pages: [
        {
          name: 'Início',
          icon: 'home',
          path: '/',
        },
        {
          name: 'Tutoriais',
          icon: 'book',
          path: '/tutoriais',
        },
      ],
      rightDrawer,
      toggleLeftDrawer() {
        rightDrawer.value = !rightDrawer.value;
      },
    };
  },
});
</script>
<style lang="scss">
.logo {
  width: 300px;
  height: 50px;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}
</style>
