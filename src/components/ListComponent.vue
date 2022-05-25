<template>
  <div class="q-pa-xs" style="max-width: 360px">
    <q-list v-for="(item, i) in lista.items" :key="i">
      <q-item v-ripple>
        <q-item-section avatar>
          <q-icon size="25px" :color="item.color" :name="item.icon" />
        </q-item-section>
        <q-item-section class="text-bold text-subtitle1 text-grey-9">
          {{ item.title }}
        </q-item-section>
      </q-item>
    </q-list>
  </div>
</template>
<script lang="ts">
import listas from '../data/listas';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ListComponent',
  components: {},
  props: {
    id: {
      type: String,
    },
  },
  setup(props) {
    const lista = listas.find((item) => item.id === props.id);
    return {
      lista,
    };
  },
});
</script>
