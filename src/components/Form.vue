<template>
    <div>
        <form @submit.prevent="dataValidation" action="" method="POST" class="margin-20">
            <fieldset>
                <legend class="legend margin-0">Tus datos</legend>
                <div class="margin-10">
                    <label for="name" class="label">Nombre y apellido</label>
                    <input type="text" name="name" placeholder="Juan Pérez" class="field">
                </div>
                <div class="margin-10">
                    <label for="phone" class="label">Celular</label>
                    <input type="text" name="phone" placeholder="3492123456" class="field"> 
                    <p class="field margin-0">Ingresá tu número de celular con el código de área, sin el 0 ni el 15.</p>
                </div>
                <div class="margin-10">
                    <label for="email" class="label">Email</label>
                    <input type="email" name="email" placeholder="ejemplo@tuemail.com" class="field">
                </div>
            </fieldset>
            <fieldset>
                <legend class="legend margin-0">Tu consulta</legend>
                <div class="margin-10">
                    <label for="subject" class="label">¿A qué área corresponde tu consulta?</label><br/>
                    <select name="subject" class="selector"> 
                        <option></option>
                        <option value="industria" class="field">Industria</option>
                        <option value="comercio" class="field">Comercio</option>
                        <option value="servicios" class="field">Servicios</option>
                        <option value="otra" class="field">Otra</option>
                    </select>
                </div>
                <div class="margin-10">
                    <label for="question" class="label">Consulta</label><br/>
                    <textarea name="question" class="field"></textarea>
                </div>
            </fieldset>
            <div class="margin-10">
                <input type="submit" value="Enviar Formulario" class="button" @click="addToTable()">
                <input type="reset" value="Limpiar Formulario" class="button">
            </div>
        </form>
        <div v-if="errors.length" class="alert margin-10">
            <h4 class="legend margin-10">¡Atención!</h4>
            <ul>
                <li v-for="(error, i) in errors" :key="i" class="field">{{error}}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Form',
    data() {
        return {
            errors: [],
            form: {
                name: "",
                phone: "",
                email: "",
                subject: "",
                question: "",
            }
        }
    },
    methods: {
        dataValidation () {
            if (this.form.name && this.form.phone && this.form.email && this.form.subject && this.form.question) {
                return true
            };
            if (this.form.name === "") {this.errors.push("Ingresá tu nombre y apellido.")};
            if (this.form.phone === "") {this.errors.push("Ingresá tu número de celular.")};
            if (this.form.email === "") {this.errors.push("Ingresá tu email.")};
            if (this.form.subject === "") {this.errors.push("Elegí un tema.")};
            if (this.form.question === "") {this.errors.push("Dejanos tu consulta.")};
        },
        addToTable() {
            this.$emit("add-to-table", this.id);
        },
    }
}
</script>

<style scoped>
    .legend {
        color: #00523F;
        font-weight: bold;
        font-size: 18px;
        text-align: left;
    }

    .field, .label {
        width: 95%;
        display: block;
        color: black;
        font-size: 15px;
        text-align: left;
        text-decoration: none;
    }

    .selector {
        display:block;
    }

    .margin-20 {
        margin: 20px;
    }

    .margin-10 {
        margin: 10px;
    }
    .margin-0 {
        margin: 0px;
    }

    .button {
    background-color: #00523F;
    border: none;
    border-radius: 5px;
    margin: 5px;
    padding: 10px;
    box-shadow: 1px 1px 3px grey;
    color: #fff;
    font-weight: bold;
    font-size: 15px;
    text-decoration: none;
    text-align: center;
    }

    .button:visited {
        color: #fff;
    }

    .button:hover {
        color: #9fe6d5;
        text-decoration: none;
    }

    .alert {
        background-color: #9fe6d5;
        padding: 20px;
    }
</style>