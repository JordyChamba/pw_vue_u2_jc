<!--html-->
<template>
    <div>
        <h1>{{ titulo2 }}</h1>
        <p>{{ numero }} <sup>2</sup>={{ calcularCuadrado }}</p> <!--Para usar JS en html-->
        <p>{{ numero }} <sup>2</sup>={{ calcularCuadrado }}</p>
        <p>{{ numero }} <sup>3</sup>={{ calcularCuadrado }}</p>
        <p>{{ numero }} <sup>2</sup>={{ calcularCubo }}</p>
        <p>{{ numero }} <sup>2</sup>={{ obtenerCubo() }}</p>

        <div>
            <button @:click="incrementar()">+1</button>
            <button @:click="decrementar()">-1</button>
            <button v-if="mostrar">Prueba</button>
        </div>
    </div>
</template>

<!--js-->
<script>
export default {

    data() {
        return {
            numero: this.inicio,
            titulo: 'Contador'
        };
    }, //Propiedades reactivas

    methods: {
        obtenerCuadrado() {
            console.log("Entro a obtener cuadrado");
            return this.numero * this.numero;
        },
        obtenerCubo() {
            console.log("Entro a obtener cubo");
            return this.numero * this.numero * this.numero;
        },
        incrementar() {
            console.log(this.titulo2);
            this.numero++;
        },

        decrementar() {
            this.numero--;
        },
    }, //metodos

    computed: {
        calcularCuadrado() {
            console.log("Entro a propiedad computada");
            return this.numero * this.numero;
        },

        calcularCubo() {
            console.log("Entro a propiedad computada cubo");
            return this.numero * this.numero * this.numero;
        },
    },
    /*props: ["titulo2", "inicio", "mostrar"], declaracion basica de props*/

    props: {
        titulo2: String,
        inicio: {
            type: Number,
            default: 99,
            validator(value) {
                return value > 10;
            },
        },
        mostrar: Boolean
    }
    /*String, Number, Boolean, Object, Date, Array, Function, BigInt */
};
</script>

<!--css-->
<style>
h1 {
    background-color: greenyellow;
    height: 40px;
    width: 200px;
}

p {
    background-color: burlywood;
    width: 70px;
}

button {
    background-color: aqua;
    height: 20px;
    width: 60px;
    border-radius: 3px;
    margin: 5px;
}
</style>