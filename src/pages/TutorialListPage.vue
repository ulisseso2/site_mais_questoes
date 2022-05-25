<template>
  <q-page class="bg-grey-1">
    <q-scroll-area style="height: calc(100vh - 70px)">
      <div
        style="height: 300px"
        class="column no-wrap flex-center bg-grey text-white q-pa-lg"
      >
        <div class="text-h2 q-pa-md text-center">Tutoriais</div>
      </div>
      <div class="row q-pa-md">
        <div
          class="col-md-3 col-sm-6 col-xs-12"
          v-for="(item, i) in tutorials"
          :key="i"
        >
          <q-card
            style="min-height: 250px"
            class="q-ma-md cursor-pointer"
            v-ripple
            @click="$router.push(`/tutoriais/${item.id}`)"
          >
            <q-card-section class="text-center q-py-lg">
              <div class="text-h6 text-bold">{{ item.title }}</div>
            </q-card-section>
            <q-separator />
            <q-card-section class="text-center q-py-lg">
              <div class="text-center text-subtitle2">
                {{ item.description }}
              </div>
            </q-card-section>
          </q-card>
        </div>
      </div>
    </q-scroll-area>
  </q-page>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

import tutorials from '../data/tutorials';

export default defineComponent({
  name: 'TutorialPage',
  components: {},
  setup() {
    return {
      slide: ref('style'),
      tutorials,
    };
  },
});
</script>
<style scoped></style>
