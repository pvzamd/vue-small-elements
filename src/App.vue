<script setup>
import { ref, reactive, watch } from 'vue';
import Buttons from './components/Buttons.vue'
import HomePages from './components/HomePages.vue'
import CheckBoxes from './components/CheckBoxes.vue'

const checkAll = ref(false);
const checkboxes = reactive([
  { checkboxValue: false },
  { checkboxValue: false },
  { checkboxValue: false }
])
const toastAlert = ref(false)

watch(checkboxes, (newVal) => {
  checkAll.value = newVal.every(checkbox => checkbox.checkboxValue)
},
{ deep: true })

const checkUpdateParent = (value) => {
  if (value.checkboxID == "allpage") {
    checkAll.value = value.checkAll
    checkboxes.forEach(element => element.checkboxValue = value.checkAll);
  }
  else{
    checkboxes[value.checkboxID].checkboxValue = value.checkAll;
    // checkAll.value = checkboxes.filter(e=>e.checkboxValue==false).length != 0 ? false: true
  }
}

const buttonClickedParent = ()=>{
  toastAlert.value = true
  setTimeout(() => {
    toastAlert.value = false
  }, 2000);
}
</script>

<template>
  <div class="app">
    <div class="container">
      <div class="pages">
        <HomePages pageName="All pages" checboxID="check1">
          <CheckBoxes checkboxID="allpage" :checkAll="checkAll" @checkUpdate="checkUpdateParent" />
        </HomePages>
        <hr />
        <template v-for="(item, index) in checkboxes" :key="index">
          <HomePages :pageName="`page ${index + 1}`">
            <CheckBoxes :checkboxID="index" :checkAll="item.checkboxValue" @checkUpdate="checkUpdateParent" />
          </HomePages>
        </template>
        <hr />
        <Buttons @buttonClickedEmit="buttonClickedParent"/>
      </div>
    </div>
  </div>
  <div class="toast" v-if="toastAlert">
    Your selection is set!!
  </div>
</template>

<style scoped>
.app, .toast {
  padding: 20px;
  font-family: "Montserrat", sans-serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
  font-size: 14px;
  color: #1F2128;
}

.container {
  padding: 10px;
  background-color: #FFFFFF;
  width: min-content;
}

.pages {
  background: #FFFFFF;
  border: 1px solid #EEEEEE;
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 8px 15px 8px 22px;
  box-shadow: 0px 8px 15px 0px #1414141F, 0px 0px 4px 0px #1414141A;
  width: min-content;
}

hr {
  /* border-top: 1px solid #EEEEEE; */
  border-top: 0.7px solid #CDCDCD
}

.single-page {
  display: flex;
  justify-content: space-between;
}
.toast{
  padding: 0 30px;
  color: rgb(16, 129, 16);
}
</style>
