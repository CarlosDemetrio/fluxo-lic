<template>
  <q-page class="flex flex-center">


    <fluxo-lic/>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import FluxoLic from "pages/fluxoLic";

export default defineComponent({
  name: 'IndexPage',
  components: { FluxoLic }

})
</script>
