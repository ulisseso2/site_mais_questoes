<template>
  <q-page>
    <div
      style="height: 250px"
      class="column no-wrap flex-center bg-grey text-white q-pa-lg relative-position"
    >
      <q-badge label="Tutorial" outline rounded size="md"></q-badge>
      <div
        class="text-h1 q-pa-md text-center"
        style="font-size: 2.5em; line-height: 1.2"
      >
        {{ tutorial.title }}
      </div>
      <q-btn
        label="Mais tutoriais"
        color="primary"
        flat
        @click="$router.push('/tutoriais')"
      ></q-btn>
    </div>
    <div class="row q-pa-md">
      <div
        :class="[`col-md-${section.col}`, 'col-sm-12', 'col-xs-12', 'q-px-md']"
        v-for="(section, s) in tutorial.sections"
        :key="s"
      >
        <q-card class="q-mx-xl" v-bind="section" v-if="section.type === 'text'">
          <q-card-section class="q-py-xs">
            <div :class="section.contentClass" :style="section.contentStyle">
              <img :src="section.src" :alt="section.src" />
              <div v-if="section.html" v-html="section.content"></div>
              <div v-else>{{ section.content }}</div>
            </div>
          </q-card-section>
        </q-card>
        <q-card
          class="q-ma-md q-px-md"
          v-bind="section"
          v-else-if="section.type === 'image'"
        >
          <div :class="section.contentClass" :style="section.contentStyle">
            <q-img
              :src="section.src"
              :ratio="section.ratio"
              :style="section.size"
            />
          </div>
        </q-card>
        <q-card
          class="q-ma-md q-px-md"
          v-bind="section"
          v-else-if="section.type === 'list'"
        >
          <div :class="section.contentClass" :style="section.contentStyle">
            <q-list dense>
              <q-item v-for="(item, i) in section.items" :key="i">
                <q-item-section avatar>
                  <q-icon :color="section.iconColor" :name="section.icon" />
                </q-item-section>
                <q-item-section>
                  {{ item }}
                </q-item-section>
              </q-item>
            </q-list>
          </div>
        </q-card>
        <q-video
          class="q-ma-md"
          v-else
          :src="section.content"
          :ratio="16 / 9"
        ></q-video>
      </div>
    </div>
    <div>
      <q-card class="my-card column items-center justify-center">
        <q-card-section class="col-8 bg-white text-center">
          <div class="text-h5 text-secondary">Esse artigo foi útil?</div>
          <div class="text-h6 text-grey-9">
            Volte aos tutoriais ou fale conosco
          </div>
        </q-card-section>
        <q-card-section class="col-8">
          <q-card-actions class="text-grey-9">
            <q-btn flat @click="$router.push('/tutoriais')">+Tutoriais</q-btn>
            <q-btn flat @click="$router.push('/contato')">Suporte</q-btn>
          </q-card-actions>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import tutorials from '../data/tutorials';
import { useRouter } from 'vue-router';

export default defineComponent({
  name: 'TutorialPage',
  components: {},
  props: {
    id: {
      type: String,
    },
  },
  setup(props) {
    const router = useRouter();
    const tutorial = tutorials.find((item) => item.id === props.id);
    if (!tutorial) {
      router.push('/tutoriais');
    }
    return {
      tutorial,
    };
  },
});
</script>
<style lang="scss" scoped></style>
