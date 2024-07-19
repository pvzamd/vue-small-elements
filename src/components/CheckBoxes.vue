<script setup>
import { defineProps, defineEmits, reactive } from "vue";

const props = defineProps({
    checkboxID: String,
    checkAll: Boolean,
});

const emit = defineEmits(["checkUpdate"]);

const toggleAll = () => emit("checkUpdate", {checkAll:!props.checkAll, checkboxID:props.checkboxID});
</script>

<template>
    <label class="check-container">
        <input class="choices" type="checkbox" :checked="checkAll" name="" :id="checkboxID" @change="toggleAll()">
        <span class="checkmark"></span>
    </label>
</template>

<style scoped>
.check-container {
    position: relative;
    padding-left: 35px;
}

.check-container input {
    width: 0;
}

.checkmark {
    position: absolute;
    top: 0;
    left: 0;
    height: 25px;
    width: 25px;
    background-color: #FFFFFF;
    border-radius: 6px;
    border: 1px solid #CDCDCD;
}

.check-container:hover input~.checkmark {
    border: 1px solid #BDBDBD;
}

.check-container input:checked~.checkmark {
    background-color: #5087F8;
}

.check-container input:checked:hover~.checkmark {
    background-color: #2469F6;
}

.checkmark:after {
    content: "";
    position: absolute;
    display: none;
}

.check-container .checkmark:after {
    left: 8px;
    top: 1px;
    width: 8px;
    height: 15px;
    border: solid #FFFFFF;
    border-width: 0 1.4px 1.4px 0;
    -webkit-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    transform: rotate(45deg);
}

.check-container:hover input~.checkmark:after {
    display: block;
    border: solid #E3E3E3;
    border-width: 0 1.4px 1.4px 0;
}

.check-container input:checked~.checkmark:after {
    display: block;
    border: solid #FFFFFF;
    border-width: 0 1.4px 1.4px 0;
}

.check-container:active input~.checkmark:after {
    display: block;
    border: solid #878787;
    border-width: 0 1.4px 1.4px 0;
}
</style>
