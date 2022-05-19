<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.png">
        <HelloWorld msg="Desafío Clase 8 Curso VueJs"/>
        <Form @add-to-table="addToTable"/>
        <Table
            v-if="requestsReceived.length"
            :name="requestsReceived.name"
            :phone="requestsReceived.phone"
            :email="requestsReceived.email"
            :subject="requestsReceived.subject"
            :question="requestsReceived.question"
        />
    </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Form from './components/Form.vue'
import Table from './components/Table.vue'

export default {
    name: 'App',
    components: {
        HelloWorld,
        Form,
        Table,
    },
        data() {
        return {
            requestsReceived: [],
        }
    },
    methods: {
        addToTable(id) {
            let newRequest = this.requestsReceived.find((item) => {
                return item.id == id;});    
                let newCopy = {...newRequest, name: form.name, phone: form.phone, email:  form.email , subject:  form.subject, question:  form.question,}; 
                this.requestsReceived.push(newCopy);
        }
    },
}
</script>

<style>
#app {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #00523F;
    margin-top: 20px;
}
img {
    width: 50px;
}
</style>
