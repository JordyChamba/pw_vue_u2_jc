<template>
    <div class="container">
        <img src="https://yesno.wtf/assets/yes/5-64c2804cc48057b94fd0b3eaf323d92c.gif" alt="Error">
        <br>
        <div class="pregunta-container">
            <input type="text" placeholder="Hazme una pregunta">
            <p>Recuerda terminar con el signo de interrogación (?)</p>
            <h2>Seré millonario?</h2>
            <h1>Yes, No</h1>
        </div>

    </div>
</template>

<script>
export default {

}
</script>

<style scoped>
h2 {
    font-size: 50px;
    color: white;
}

h1 {
    color: white;
    margin-top: 150px;
}

p {
    color: white;
    font-size: 20px;
}

input {
    color: white;
    background: rgba(255, 255, 255, 0.2);
    border: 2px solid white;
    padding: 15px;
    font-size: 18px;
    border-radius: 10px;
    width: 350px;
}

input::placeholder {
    color: rgba(255, 255, 255, 0.7);
}

img {
    width: 100vw;
    height: 100vh;
    max-height: 100%;
    max-width: 100%;
    position: fixed;
    left: 0px;
    top: 0px;
}

.pregunta-container {
    position: relative;
    top: 50%;
    border: 3px solid white;
    padding: 40px;
    background: rgba(0, 0, 0, 0.3);
    border-radius: 20px;
    max-width: 600px;
    margin: 0 auto;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
}
</style>