<template>
  <nav class="menu">
    <ul class="menu__list">
      <li class="menu__item">
        <nuxt-link to="/" class="menu__link">Главная</nuxt-link>
      </li>
      <li class="menu__item">
        <nuxt-link to="/stories" class="menu__link">Истории</nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {};
</script>

<style scoped>
.menu__list {
  list-style-type: none;
  display: flex;
  padding: 0;
}

.menu__item {
  margin-right: 40px;
}

.menu__link {
  color: black;
  font-weight: normal;
  font-size: 18px;
  line-height: 24px;
  text-decoration: none;
  transition: opacity 0.3s;
}

.menu__link.nuxt-link-exact-active {
  text-decoration: underline;
}

.menu__link.nuxt-link-exact-active:hover {
  opacity: 1;
}

.menu__link:hover {
  opacity: 0.8;
}

.menu__item:last-child {
  margin-right: 0;
}

@media (max-width: 1350px) {
  .menu__link {
    font-size: 16px;
  }
}

@media (max-width: 1250px) {
  .menu__item {
    margin-right: 30px;
  }
}

@media (max-width: 1000px) {
  .menu__list {
    flex-direction: column;
  }

  .menu__item {
    margin-left: 0;
    margin-bottom: 18px;
  }

  .menu__item:last-child {
    margin-bottom: 0;
  }
}

@media (max-width: 700px) {
  .menu__item {
    margin-left: 0;
    margin-bottom: 18px;
  }

  .menu__item:last-child {
    margin-bottom: 0;
  }
}
</style>
