<template>
  <q-card class="main-card">
    <q-card-section :class="bgColor" class=" text-center text-white card-title flex justify-between  content-center">
      <span >{{ codigoSigaa }}</span>
      <q-separator class="q-mx-md" vertical color="dark-blue" size="2px" />
      <span > {{ creditos }}</span>
    </q-card-section>
    <q-separator />
    <q-card-section class="bg-grey-2 q-mt-none content-card flex flex-center">
      <div class="ellipsis-3-lines text-center">{{ nome }}</div>
      <span v-if="cadeiaSeletiva" class="text-left text-weight-bold">Cadeia Seletiva: {{ cadeiaSeletiva}}</span>
    </q-card-section>

  </q-card>
</template>

<script>
export default {
  name: 'cardDisciplina',
  data () {
    return {
      bgColor: this.siglaDepartamento === 'CIC' ? 'bg-primary' : this.siglaDepartamento === 'MAT' || this.siglaDepartamento === 'EST' ? 'bg-red' : this.siglaDepartamento === 'LIC' ? 'bg-teal' : 'bg-accent'
    }
  },
  props: {
    nome: { type: String },
    codigoSigaa: { type: String },
    creditos: { type: String },
    siglaDepartamento: { type: String },
    tipo: { type: String },
    cadeiaSeletiva: {type: Number}
  }
}
</script>

<style lang="scss">
  .main-card {
    width: 13em;
  }
  .content-card {
    height: 6em;
    font-size: 10px;
    font-weight: bold;
  }
  .card-title {
    font-size: 11px;
    height: 20px
  }

</style>
