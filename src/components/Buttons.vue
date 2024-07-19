<script setup>
import { defineEmits } from "vue";
const emit = defineEmits(["buttonClickedEmit"]);
const buttonClicked = () => emit("buttonClickedEmit");
</script>

<template>
    <div class="button-container">
    <button class="button-done" @click="buttonClicked()">Done</button>
    </div>
</template>

<style scoped>
.button-container{

}
.button-done{
    font-family: "Montserrat", sans-serif;
    font-optical-sizing: auto;
    font-weight: 400;
    font-size: 14px;
    font-style: normal;
    height: 40px;
    width: -webkit-fill-available;
    border-radius: 4px;
    outline: none;
    border: none;
    background-color: #FFCE22;
}
.button-done:hover{
    background-color: #FFD84D;
}
.button-done:active{
    background-color: #FFCE22;
}
</style>
