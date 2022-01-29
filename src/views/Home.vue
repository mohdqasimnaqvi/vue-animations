<template>
  <div class="home">
   <transition name="toast"> 
    <Toast v-if="showToast" />
   </transition>
    <Todos @badValue="triggerToast" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Toast from '../components/Toast'
import Todos from '../components/Todos'
const showToast = ref(false)
const showP = ref(false);

const triggerToast = () => {
  showToast.value = true;
  setTimeout(() => showToast.value = false, 3000)
}
</script>

<style>
  .toast-enter-from {
    opacity: 0;
    transform: translateY(-60px);
  }
  .toast-enter-active {
    animation: wobble 0.5s ease
  }
  .toast-leave-active {
    transition: 0.3s ease;
  }
  .toast-leave-to {
    opacity: 0;
    transform: translateY(-60px)
  }
  @keyframes wobble {
    0% {
      transform: translateY(-60px);
      opacity: 0;
    }
    50% {
      transform: translateY(0px);
      opacity: 1;
    }
    60% {
      transform: translateX(8px);
    }
    70% {
      transform: translateX(-8px);
    }
    80% {
      transform: translateX(4px);
    }
    90% {
      transform: translateX(-4px);
    }
    100% {
      transform: translateX(0);
    }
  }
</style>