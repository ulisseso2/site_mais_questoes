<template>
  <q-page>
    <div class="bg-secondary">
      <div class="row justify-center items-center q-pt-md">
        <div class="col-xs-12 col-sm-12 col-md-5">
          <headings-home id="main" />
        </div>
        <div class="col-xs-12 col-sm-12 col-md-5">
          <q-img :src="pcImage" />
        </div>
      </div>
    </div>
    <headings-home id="solucao" />

    <section-cards id="deals" />

    <div class="row justify-center q-my-xl items-center">
      <div class="col-xs-12 col-sm-12 col-md-4 bg-secondary">
        <q-img class="imgAluno" :src="alunoPc" />
      </div>
      <div class="col-xs-12 col-sm-12 row col-md-7 items-center q-pa-xs">
        <headings-home id="mais" />
        <p class="q-px-xl q-mx-xl text-subtitle1">
          Para os alunos, somos um aliado que realiza em poucos minutos, o que
          ele levaria meses para conseguir: avaliações, questões, planos de
          estudo, simulados.
        </p>
        <p class="q-px-xl q-mx-xl text-subtitle1">
          Para as instituições, somos uma plataforma que auxilia no controle do
          desenvolvimento do aluno, no desempenho em cada disciplina, nas
          chances de aprovação, nas técnicas e planos de estudo, na avaliação
          global da instituição.
        </p>
      </div>
    </div>

    <paralax-title
      :height="200"
      title="Benefícios para todas as etapas do seu negócio"
    />

    <section-cards id="features" />
    <headings-home id="manager" />

    <div class="row justify-center q-mb-xl items-center">
      <q-img
        class="col-xs-12 col-sm-12 col-md-6"
        src="https://static-maisquestoes.s3.us-east-2.amazonaws.com/proficiencia-mais.png"
      />
      <div
        class="col-xs-12 col-sm-12 justify-center items-center row col-md-4 q-pa-xs"
      >
        <list-component id="manager" />
        <button-contact colorButton="secondary" />
      </div>
    </div>

    <div class="row justify-center items-center">
      <div class="column col-xs-12 items-center col-sm-12 col-md-5 q-pa-xs">
        <headings-home id="plan" />
        <list-component id="questions" />
      </div>
      <q-img
        class="col-xs-12 col-sm-12 col-md-5"
        src="https://static-maisquestoes.s3.us-east-2.amazonaws.com/proeficiencia2-1.png"
      />
    </div>

    <headings-home id="suport" />
    <section-cards id="suport" />
  </q-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SectionCards from '../components/templates/SectionCards.vue';
import HeadingsHome from '../components/templates/HeadingsHome.vue';
import ParalaxTitle from '../components/templates/SectionParalax.vue';
import ButtonContact from '../components/buttonContact.vue';
import ListComponent from '../components/ListComponent.vue';
import pcImage from '../assets/images/pc_site.png';
import alunoPc from '../assets/images/aluno-pc.jpg';
import diretorPc from '../assets/images/diretor-pc.jpg';
import mesaPcs from '../assets/images/mesa-pcs.jpg';

export default defineComponent({
  name: 'indexPage',
  components: {
    HeadingsHome,
    SectionCards,
    ParalaxTitle,
    ListComponent,
    ButtonContact,
  },
  setup() {
    return {
      pcImage,
      alunoPc,
      diretorPc,
      mesaPcs,
    };
  },
});
</script>
<style lang="scss" scoped>
.imgAluno {
  opacity: 0.7;
}
</style>
