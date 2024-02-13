<script setup>
import DefaultButton from '../components/DefaultButton.vue'
import { shallowRef } from 'vue'


const components = shallowRef([DefaultButton])
const currentComponent = shallowRef()

function selectComponent(event) {
  const component = components.value.find(c => c.__name === event.target.innerText)
  currentComponent.value = component
}
</script>

<template>
  <div id="page-container">
    <header id="header">
      <h1>Componentes</h1>
      <div id="component-list">
        <p class="tabs" v-for="component in components" :key="component" @click="selectComponent">{{ component.__name }}</p>
      </div>
    </header>
    <div id="demo-container">
      <div id="component-container">
        <component :is="currentComponent" />
      </div>
    </div>
  </div>
</template>

<style scoped>
#page-container {
  background-color:#FFF3CF;
  height: 100vh;
}

#header {
  background-color: #C9D7DD;
  padding: 20px;
  text-align: center;
}

#demo-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}

#component-container {
  display: flex;
  justify-content: center;
  align-items: center;
  border: solid 1px #aaaaaa;
  width: 1000px;
  height: 700px;
  margin-top: 20px;
  background-color: #E8C872;
  text-align: center;
  font-size: 20px;
  font-weight: bold;
  border-radius: 10px;
  box-shadow: 0 0 10px #aaaaaa;
  transition: all 0.3s;
}

#component-list {
  display: flex;
  justify-content: center;
  margin-top: 20px;
  gap: 20px;
}

.tabs {
  cursor: pointer;
  font-size: 20px;
  font-weight: bold;
  color: #637A9F;
  transition: all 0.3s;
}

.tabs:hover {
  color: #E8C872;
}

</style>