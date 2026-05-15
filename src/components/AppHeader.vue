<template>
  <header class="header-container">
    <div class="header-top">
      <div class="titles">
        <h1>Моє Портфоліо</h1>
        <p>Вітаю на моїй особистій сторінці.</p>
      </div>
      
      <button class="burger" @click="menuOpen = !menuOpen">
        {{ menuOpen ? '✖' : '☰' }}
      </button>
    </div>

    <button @click="$emit('toggle-theme')" class="btn theme-btn">Змінити тему</button>

    <nav :class="['nav-menu', { open: menuOpen }]" aria-label="Навігація">
      <ul>
        <li><RouterLink to="/" @click="menuOpen = false">Головна</RouterLink></li>
        <li><RouterLink to="/contacts" @click="menuOpen = false">Контакти</RouterLink></li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { ref } from 'vue'; // Імпортуємо ref для створення реактивної змінної [cite: 457]
import { RouterLink } from 'vue-router';

defineEmits(['toggle-theme']);

// Реактивна змінна для керування станом меню (відкрито/закрито) 
const menuOpen = ref(false); 
</script>

<style scoped>
.header-container {
  margin-bottom: 20px;
}

.header-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* Ховаємо кнопку-бургер на десктопі [cite: 488] */
.burger {
  display: none; 
  background: none;
  border: none;
  font-size: 32px;
  cursor: pointer;
  color: var(--text-color);
}

.nav-menu ul {
  display: flex;
  justify-content: center;
  gap: 20px;
  list-style: none;
  padding: 15px;
  background-color: var(--card-bg);
  border-radius: 8px;
  margin-bottom: 30px;
  transition: background-color 0.3s;
}

.nav-menu a.router-link-active {
  border-bottom: 2px solid var(--primary);
  padding-bottom: 2px;
}

/* --- АДАПТИВНІСТЬ (Media Queries) --- */
/* Точка зламу для планшетів та телефонів [cite: 489] */
@media (max-width: 768px) {
  .burger {
    display: block; /* Показуємо бургер [cite: 490] */
  }

  .nav-menu ul {
    display: none; /* Ховаємо стандартне горизонтальне меню [cite: 492] */
    flex-direction: column; /* Вибудовуємо елементи вертикально [cite: 493] */
    align-items: center;
    padding: 10px;
  }

  /* Якщо меню відкрите (є клас open), показуємо його [cite: 498] */
  .nav-menu.open ul {
    display: flex; 
  }
  
  /* Робимо кнопку зміни теми на всю ширину для зручності на телефоні */
  .theme-btn {
    width: 100%; 
  }
}
</style>