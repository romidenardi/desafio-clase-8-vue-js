<template>
    <table>
        <thead>
            <tr>
                <th>Nombre y apellido</th>
                <th>Celular</th>
                <th>Email</th>
                <th>Tema</th>
                <th>Consulta</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(request, i) in requests" :key="i">
                <th v-for="(name, n) in request" :key="n">{{name}}</th>
                <th v-for="(phone, p) in request" :key="p">{{phone}}</th>
                <th v-for="(email, em) in request" :key="em">{{email}}</th>
                <th v-for="(subject, s) in request" :key="s">{{subject}}</th>
                <th v-for="(question, q) in request" :key="q">{{question}}</th>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    name: 'Table',
    props: {
        name: {
            type: String,
            required: true,
        },
        phone: {
            type: String,
            required: true,
        },
        email: {
            type: String,
            required: true,
        },
        subject: {
            type: String,
            required: true,
        },
        question: {
            type: String,
            required: false,
        },
    },
}
</script>

<style>
    table {
        margin: 5px;
        padding: 5px;
        background-color: #9fe6d5;
    }

    thead tr th {
        font-size: 14px;
        font-weight: bold;
        padding: 5px;
        color: #008767;
    }

    tbody tr th {
        font-size: 14px;
        font-weight: normal;
        padding: 5px;
    }
</style>