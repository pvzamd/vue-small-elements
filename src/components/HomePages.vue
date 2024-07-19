<script setup>
import CheckBoxes from './CheckBoxes.vue'
import { defineProps, reactive } from "vue";

const props = defineProps({
    pageName: String,
    checkboxID: String,
});
</script>

<template>
<div class="each-page">
    <div class="all-pages">{{ pageName }}<slot/></div>
    <Buttons/>
</div>
</template>

<style scoped>
.each-page{
    
}
.all-pages{
    width: 370px;
    display: flex;
    align-items:center;
    justify-content: space-between;
    background-color: #FFFFFF;
}
</style>
