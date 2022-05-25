<template>
  <div v-for="(detail, i) in heading.details" :key="i">
    <q-card :class="[`my-card q-pa-xl bg-${detail.bg} no-shadow`]">
      <q-card-section
        :class="[`column q-ma-none q-pa-xs text-${detail.text_align}`]"
      >
        <h2
          :class="[
            `col-8 text-${detail.sizeT} , text-${detail.colorT} text-bold q-ma-xs q-px-xl`,
          ]"
        >
          {{ detail.title }}
        </h2>
        <h3
          :class="[
            `text-${detail.sizeS} , text-${detail.colorS} q-ma-xs q-px-xl`,
          ]"
        >
          {{ detail.subtitle }}
        </h3>
      </q-card-section>
    </q-card>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import headings from '../../data/headings';

export default defineComponent({
  name: 'HeadingsHome',
  components: {},
  props: {
    id: {
      type: String,
    },
  },
  setup(props) {
    const heading = headings.find((item) => item.id === props.id);
    return {
      heading,
    };
  },
});
</script>
