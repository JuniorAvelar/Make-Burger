<template>
    <div class="message-container">
        <p>{{ msg }}</p>
    </div>
</template>


<script>    
    export default {
        name: "Message",
        props: {
            msg: String
        }
    }
</script>

<style scoped>

.message-container {
    color: #004085;
    background-color: #cce5ff;
    border: solid 2px #b8daff;
    border-radius: 5px;
    padding: 10px;
    max-width: 400px;
    margin: 30px auto;
}

.message-container p {
    text-align: center;
}
</style>