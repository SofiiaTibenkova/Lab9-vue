<template>
  <header>
    <h1>Моє Портфоліо</h1>
    <p>Вітаю на моїй особистій сторінці.</p>
    
    <button @click="$emit('toggle-theme')" class="btn">Змінити тему</button>
    
    <nav aria-label="Навігація">
      <ul>
        <li><RouterLink to="/">Головна</RouterLink></li>
        <li><RouterLink to="/contacts">Контакти</RouterLink></li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { RouterLink } from 'vue-router';

defineEmits(['toggle-theme']);
</script>

<style scoped>
nav ul {
    display: flex;
    justify-content: center;
    gap: 20px;
    list-style: none;
    padding: 15px;
    background-color: var(--card-bg);
    border-radius: 8px;
    margin-bottom: 30px;
}

nav a.router-link-active {
    border-bottom: 2px solid var(--primary);
    padding-bottom: 2px;
}
</style>