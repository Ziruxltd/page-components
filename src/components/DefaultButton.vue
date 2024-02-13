<template>
    <button 
      class="default-button"
    >
      {{ label }}
    </button>
  </template>
  
  <script setup>
  import { defineProps, watchEffect } from 'vue'
  
  const props = defineProps({
    label: {
      type: String,
      default: 'Label',
    },
    color: {
      type: String,
      default: '#637A9F'
    },
    hoverColor: {
      type: String,
      default: '#E8C872',
    }
  })
  
  watchEffect(() => {
    document.documentElement.style.setProperty('--button-color', props.color)
    document.documentElement.style.setProperty('--button-hover-color', props.hoverColor)
  })
  </script>
  
  <style scoped>
  .default-button {
    padding: 10px 20px;
    font-size: 16px;
    border-radius: 8px;
    cursor: pointer;
    background-color: var(--button-color);
    border: none;
  }
  
  .default-button:hover {
    background-color: var(--button-hover-color);
  }
  </style>