<template>
    <div id="burguer-table">
        <div>
            <div id="burger-table-heading">
                <div class="order-id"> N°</div>
                <div>Cliente:</div>
                <div>pão:</div>
                <div>carne:</div>
                <div>opcionias:</div>
                <div>Ações:</div>
            </div>

            <div id="burger-table-rows">
                <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
                    <div class="order-number">{{ burger.id }}</div>
                    <div>{{ burger.nome }}</div>
                    <div>{{ burger.pao }}</div>
                    <div>{{ burger.carne }}</div>
                    <div>
                        <ul>
                            <li v-for="(opcional , i) in burger.opcionais" :key="i">{{ opcional }}</li>
                           
                        </ul>
                    </div>
                    <div>
                        <select name="status" class="status">
                            <option value="">Selecione</option>
                            <!-- "A propriedade selected será verdadeira se burger.status for igual a status.tipo." -->
                            <option v-for="status in status" value="" :key="status.id" :selected="burger.status == status.tipo">  {{ status.tipo }}</option>
                        </select>
                        <button class="delet-btn">Cancelar</button>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
    export default {
        name: 'Dashboard',
        data() {
            return {
                burgers: null, 
                burger_id: null,
                status: [] ,
            }
        },
        
        methods: {
            async getPedidos() {
                const req = await fetch("http://localhost:3000/burgers")

                const data = await req.json()

                this.burgers = data

                this.getStatus()
            },

            async getStatus() {
                const req = await fetch('http://localhost:3000/status')

                const data = await req.json()

                this.status = data
                console.log(data)
            }
        },

        mounted() {
            this.getPedidos()
        }

    }
</script>

<style scoped>
    #burger-table {
        max-width: 1200px;
        margin: 0 auto;
    }

    #burger-table-heading,
    #burger-table-rows,
    .burger-table-row {
        display: flex;
        flex-wrap: wrap;
    }

    #burger-table-heading {
        font-weight: bold;
        padding: 12px;
        border-bottom: 2px solid #333;
    }

    #burger-table-heading div,
    .burger-table-row div{
        width: 19%;
    }

    .burger-table-row {
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid  #ccc;
    }

    #burger-table-heading .order-id,
    .burger-table-row .order-number{
        width: 5%;
    }

    select {
        padding: 12px 6px;
        margin-right: 12px;
    }

    .delet-btn {
        background-color: #222;
        color: #fcba03;
        border: solid 2px #222;
        font-weight: bold;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .4s;
    }

    .delet-btn:hover {
        background-color: transparent;
        color: #222;
    }
</style>