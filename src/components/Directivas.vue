<template>
    <div class="form-container">
        <div class="form-group">
            <label for="id_nombre">Nombre</label>
            <input id="id_nombre" type="text" v-model="nombre" />
        </div>

        <div class="form-group">
            <label for="id_apellido">Apellido</label>
            <input id="id_apellido" type="text" v-model="apellido" />
        </div>

        <div class="buttons">
            <button @click="imprimirNombre()">Imprimir Nombre</button>
            <button @click="imprimirApellido()">Imprimir Apellido</button>
            <button @click="agregarEstudiante()">Agregar estudiante</button>
        </div>

        <p v-if="mensaje" class="mensaje">{{ mensaje }}</p>

        <h2>Estudiantes agregados</h2>

        <ul v-if="arreglo.length">
            <li v-for="(estu, index) in arreglo" :key="index">
                {{ estu.nombre }} {{ estu.apellido }}
            </li>
        </ul>

        <p v-else>No hay estudiantes aún.</p>

        <table v-if="arreglo.length" border="1">
            <thead>
                <tr>
                    <th>Nombre</th>
                    <th>Apellido</th>
                </tr>
            </thead>

            <tbody>
                <tr v-for="(estu, index) in arreglo" :key="index">
                    <td>{{ estu.nombre }}</td>
                    <td>{{ estu.apellido }}</td>
                </tr>
            </tbody>

        </table>
    </div>
</template>


<script>
export default {
    data() {
        return {
            nombre: "",
            apellido: "",
            arreglo: [],
            mensaje: "",
        };
    },

    methods: {
        imprimirNombre() {
            console.log(this.nombre);
        },

        imprimirApellido() {
            console.log(this.apellido);
        },

        mostrarMensaje(texto) {
            this.mensaje = texto;

            setTimeout(() => {
                this.mensaje = "";
            }, 3000);
        },

        agregarEstudiante() {
            if (!this.nombre.trim() || !this.apellido.trim()) {
                this.mostrarMensaje("Debes completar ambos campos.");
                return;
            }

            const estu = {
                nombre: this.nombre.trim(),
                apellido: this.apellido.trim(),
            };

            console.log("Se agrega estudiante", estu);

            this.arreglo.push(estu);
            this.limpiarFormulario();
            this.mostrarMensaje("Estudiante agregado correctamente!");
        },

        limpiarFormulario() {
            this.nombre = "";
            this.apellido = "";
        },
    },
};
</script>

<style scoped>
.form-container {
    max-width: 400px;
    margin: auto;
    font-family: sans-serif;
}

.form-group {
    margin-bottom: 10px;
}

input {
    width: 100%;
    padding: 6px;
}

.buttons button {
    margin-right: 10px;
    margin-top: 10px;
}

.mensaje {
    margin-top: 10px;
    font-weight: bold;
    color: red;
}
</style>