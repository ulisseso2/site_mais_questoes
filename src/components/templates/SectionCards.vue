<template>
  <div class="q-pa-xs row items-center justify-center q-ma-xs q-gutter-md">
    <div v-for="(item, i) in card.items" :key="i">
      <q-card class="my-card q-mx-xs my-custom-card">
        <q-card-section class="text-center">
          <q-icon :name="item.icon" :color="item.color" size="50px" />
        </q-card-section>
        <q-card-section class="text-center">
          <div class="text-subtitle1 text-grey-9">{{ item.description }}</div>
        </q-card-section>
        <q-card-section v-if="item.detail" class="text-center">
          <div class="text-subtitle2 text-grey-9">{{ item.detail }}</div>
        </q-card-section>
      </q-card>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import cards from '../../data/cards';

export default defineComponent({
  name: 'SectionCards',
  components: {},
  props: {
    id: {
      type: String,
    },
  },
  setup(props) {
    const card = cards.find((item) => item.id === props.id);
    return {
      card,
    };
  },
});
</script>

<style lang="sass" scoped>
.my-custom-card
  width: 200px
  min-height: 200px
</style>
