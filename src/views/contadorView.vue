<template>
    <div>
        <contador titulo2="Contador 1" :inicio="20" :mostrar="true" />
        <contador titulo2="Contador 2" :inicio="4" :mostrar="false" />
    </div>
</template>

<script>
import contador from '../components/contador.vue';
export default {
    components: {
        contador,
    },
};
</script>

<style></style>