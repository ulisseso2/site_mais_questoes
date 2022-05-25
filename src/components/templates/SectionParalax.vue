<template>
  <div :class="[`bg-${bgColor}`]">
    <q-parallax :height="height">
      <template v-slot:media>
        <img class="my-custom-image" :src="mesaPcs" />
      </template>
      <template v-slot:content="scope">
        <div
          class="absolute column items-center"
          :style="{
            opacity: 0.6 + (1 - scope.percentScrolled) * 0.4,
            top: scope.percentScrolled * 20 + '%',
            left: 0,
            right: 0,
          }"
        >
          <img :src="logoImageSrc" style="width: 250px" />
          <div class="text-h4 text-white text-center">
            {{ title }}
          </div>
        </div>
      </template>
    </q-parallax>
  </div>
</template>

<script lang="ts">
import mesaPcs from '../../assets/images/mesa-pcs.jpg';
export default {
  props: {
    bgColor: {
      type: String,
      default: 'secondary',
    },
    height: {
      type: Number,
      default: 180,
    },
    logoImageSrc: {
      type: String,
      default:
        'https://static-maisquestoes.s3.us-east-2.amazonaws.com/logo-white.png',
    },
    title: {
      type: String,
    },
  },
  setup() {
    return {
      mesaPcs,
    };
  },
};
</script>

<style lang="sass" scoped>
.my-custom-image
  filter: blur(1px)
  opacity: 0.5
</style>
