<template>
  <div class="q-pa-md q-gutter-sm">
    <q-btn
      label="Entre em Contato"
      @click="linkClick"
      glossy
      rounded
      :color="colorButton"
      class="contactButton text-subtitle1"
    />
  </div>
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
<style scoped>
.contactButton {
  width: 100%;
}
</style>
