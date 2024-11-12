<template>
  <div id="app">
    <h1> Problema de Monty Hall</h1>
    <!-- Vue recomenda usar kebab-case em templates HTML.-->
    <div class="form">
        <div v-if="!started">
        <label for= "amountDoors"> Quantas portas? </label>
        <input type="text" id="amountDoors" size="3" v-model.number="amountDoors">
        </div>
        <div v-if="!started">
        <label for= "selectedDoor"> Qual é a porta com prémio? </label>
        <input type="text" id="selectedDoor" size="3" v-model.number="selectedDoor">
        </div>

        <button v-if="!started" @click="started = true"> Iniciar </button>
        <button v-if="started" @click="started = false"> Reiniciar </button>
    </div>

    <div class="doors" v-if="started">
        <div v-for="i in amountDoors" :key="i">
            <TheDoor :hasGift="i == selectedDoor" :number="i"/>
        </div>
    </div>

  </div>
</template>

<script>
import TheDoor from './components/the-door.vue';


export default {
name:'App',
components: {TheDoor},
data () {
    return {
        started: false,
        amountDoors: 3,
        selectedDoor: null,
    }
}



}
</script>

<style>
*{
    box-sizing: border-box;
    font-family: 'Montserrat',sans-serif;
}

body {
    color: #fff;
    background: linear-gradient(to right, #28a745, #007bff)
}

#app{
    display: flex;
    flex-direction: column;
    align-items: center;
}

#app h1 {
    border: 1px solid #000;
    background-color:rgba(0, 0, 0, 0.25);
    padding: 20px;
    margin-bottom: 60px;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}
.form, .form input, .form button {
    margin-bottom: 10px;
    font-size: 2rem;
} 

.doors {
    align-self: stretch;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}
</style>