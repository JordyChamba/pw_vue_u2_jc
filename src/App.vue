<template>
  <div>
    <!--contadorView />-->
    <!--DirectivasView />-->
    <PreguntaView />
  </div>
</template>

<script>
import contadorView from './views/contadorView.vue';
import DirectivasView from './views/DirectivasView.vue';
import PreguntaView from './views/PreguntaView.vue';
export default {
  components: {
    contadorView, DirectivasView, PreguntaView,
  }
}
</script>

<style></style>