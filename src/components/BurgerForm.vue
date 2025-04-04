<template>
    <div>
        <div>
            <Message :msg="msg" v-show="msg"/>
            <form id="burger-form" @submit="createBurger">
                <div class="input-container">
                    <label for="name">Nome do clinte:</label>
                    <input type="text " name="name" id="name" v-model="name" placeholder="Digite seu nome">
                </div>

                <div class="input-container">
                    <label for="pao">Escolha a pao do seu Burger:</label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="">Selecione seu pão</option>
                        <option :value="pao.tipo" v-for="pao in paes" :key="pao.id"> {{ pao.tipo }} </option>
                    </select>
                </div>

                <div class="input-container">
                    <label for="carne">Escolha a carne do seu Burger:</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value="">Selecione sua carne</option>
                        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                    </select>
                </div>

                <div class="checkbox-control">
                    <div class="input-container" id="opcionais-container">
                    <label id="opcionais-title" for="opcionais">Selecione os opcionais:</label>
                    <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                        <div class="input-control">
                            <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                            <span>{{ opcional.tipo }}</span>
                        </div>
                    </div>
                </div>

                </div>
                <div class="input-container">
                    <input type="submit" class="submit-btn" value="Criar meu Burger">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import Message from './Message.vue'
    export default {
        name: 'BurgerForm',
        components: {
            Message
        },

        data() {
            return {
                paes: null,
                carnes: null,
                opcionaisdata:null,
                name:null,

                pao:null,
                carne:null,
                opcionais: [],
                status:"Solicitado",
                msg:null
            }
        },
        methods: {
            async getIngredientes() {
                const req = await fetch("http://localhost:3000/ingredientes")
                const  data = await req.json()
                this.paes = data.paes
                this.carnes = data.carnes
                this.opcionaisdata = data.opcionais
            },
            async createBurger(e) {
                e.preventDefault()
                const data = {
                    nome: this.name,
                    carne: this.carne,
                    pao: this.pao,
                    opcionais: Array.from(this.opcionais),
                    status: "Solocitado"
                }
                // Enviando dados para o banco
                const dataJson = JSON.stringify(data)
                const req = await fetch("http://localhost:3000/burgers", {
                    method: "POST",
                    headers: {"Content-Type": "aplication/json"},
                    body: dataJson
                })

                const res = await req.json()

                // msg do sistema
                this.msg = "Pedido feito com sucesso!"

                // limpar msg
                setTimeout(() => this.msg = null , 4000)

                // limpar campos 
                this.name = ""
                this.carne = ""
                this.pao = ""
                this.opcionais = ""
            }
        },
        mounted() {
            this.getIngredientes()
        }
    }
</script>

<style scoped>
    #burger-form {
        max-width: 400px;
        margin: 0 auto;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .input-container {
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }

    .input-container label {
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid #fcba03;
    }

    input, select {
        padding: 5px 10px;
        width: 300px;
    }

    #opcionais-container {
        flex-direction: row;
        flex-wrap: wrap; 
       }

    #opcionias-title {
        width: 100%;
    }

    .checkbox-container {
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }

    .checkbox-container span,
    .checkbox-container input {
        width: auto;
    }

    .checkbox-container span {
        margin-left: 6px;
        font-weight: bold;
    }


    .submit-btn {
        background-color: #222;
        color: #fcba03;
        font-weight: bold;
        border: solid 2px #222;
        font-size: 16px;
        padding: 10px;
        cursor: pointer;
        transition: .5s;
    }

    .submit-btn:hover {
        background-color: transparent;
        color: #222;
    }

    .input-control {
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .checkbox-control { 
        width: 76%;
    }

    
</style>