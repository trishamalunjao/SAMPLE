<template>
    <nav class="navbar">
      <img src="../../assets/images/w1-logo.png" alt="Logo" style=" height: 55px; width: auto; margin-left: 25px;">
      <div class="navbar-brand">
        <a class="navbar-item" href="#">
        </a>
      </div>
      <div class="navbar-end">
        <a class="navbar-item text-light" @click="toggleNotifications">
          <span class="icon">
            <i class="fas fa-bell"></i>
          </span>
        </a>
        <!-- <a class="navbar-item text-light" @click="toggleProfile">
          <span class="icon">
            <i class="fas fa-user"></i>
          </span>
        </a> -->
      </div>
    </nav>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const notificationsVisible = ref(false)
  const profileVisible = ref(false)
  
  const toggleNotifications = () => {
    notificationsVisible.value = !notificationsVisible.value
  }
  
  const toggleProfile = () => {
    profileVisible.value = !profileVisible.value
  }
  </script>
  