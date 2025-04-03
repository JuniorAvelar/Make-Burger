<template>
    <div>
        <p>componente de msg</p>
        <div>
            <form id="burger-form">
                <div class="input-container">
                    <label for="name">Nome do clinte:</label>
                    <input type="text " name="name" id="name" v-model="name" placeholder="Digite seu nome">
                </div>

                <div class="input-container">
                    <label for="pao">Escolha a pao do seu Burger:</label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="">Selecione seu pão</option>
                    </select>
                </div>

                <div class="input-container">
                    <label for="carne">Escolha a carne do seu Burger:</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value="">Selecione sua carne</option>
                    </select>
                </div>

                <div class="input-container" id="opcionais-container">
                    <label id="opcionais-title" for="opcionais">Selecione os opcionais:</label>
                    <div class="checkbox-container">
                        <div class="input-control">
                            <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                            <span>salame</span>
                        </div>
                    </div>

                    <div class="checkbox-container">
                        <div class="input-control">
                            <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                            <span>salame</span>
                        </div>
                    </div>

                    <div class="checkbox-container">
                        <div class="input-control">
                            <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                            <span>Molho especial</span>
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
    export default {
        name: 'BurgerForm'
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
</style>