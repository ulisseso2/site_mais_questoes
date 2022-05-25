<template>
  <q-page-sticky position="bottom-right" :offset="[18, 18]">
    <q-btn @click="linkClick" round icon="whatsapp" color="green" size="20px" />
  </q-page-sticky>
</template>

<script lang="ts">
import { openURL } from 'quasar';

const WHATSAPP_LINK =
  'https://wa.me/5521964850880?text=Quero+saber+mais+sobre+Mais+Quest%C3%B5es.';

export default {
  props: {
    colorButton: { type: String, default: 'primary' },
  },
  setup() {
    const linkClick = () => {
      return openURL(WHATSAPP_LINK);
    };
    return { linkClick };
  },
};
</script>
<style scoped></style>
