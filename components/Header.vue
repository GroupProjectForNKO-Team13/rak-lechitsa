<template>
  <header class="main-header">
    <header-content class="main-header__content">
      <nuxt-link to="/" class="main-header__logo-container">
        <h3 class="main-header__logo">{{ blockHeader.title }}</h3>
      </nuxt-link>
      <div class="main-header__container">
        <main-menu class="main-header__menu" />
        <header-button
          class="main-header__button"
          :text="textButtonMenu"
          @btnClick="toggleStoryPopup"
        />
      </div>
      <mobile-icon class="main-header__mobile-icon" />
    </header-content>
  </header>
</template>

<script>
import Content from '@/components/ui/Content';
import Menu from '@/components/ui/Menu';
import Button from '@/components/ui/Button';
import MobileIcon from '@/components/ui/MobileIcon';
export default {
  components: {
    'header-content': Content,
    'main-menu': Menu,
    'header-button': Button,
    'mobile-icon': MobileIcon,
  },
  computed: {
    blockArr() {
      return this.$store.getters['blocks/getBlockArr'];
    },
    blockHeader() {
      return this.blockArr.find(el => el.block === 'header');
    },
  },
  methods: {
    toggleStoryPopup() {
      this.$store.commit('form/finishFalse');
      this.$store.commit('popup/toggleStoryPopup');
    },
  },
  data() {
    return {
      textButtonMenu: 'Рассказать историю',
    };
  },
};
</script>

<style scoped>
.main-header {
  margin: 0 auto;
  padding: 18px 60px 18px;
  background-color: white;
  align-items: center;
  min-height: 76px;
  border-bottom: 1px solid #efefef;
}

.main-header__content {
  display: flex;
  justify-content: space-between;
}

.main-header__logo {
  width: 290px;
  font-weight: 600;
  font-size: 16px;
  line-height: 24px;
  color: black;
}

.main-header__logo-container {
  text-decoration: none;
  display: flex;
  align-items: center;
}

.main-header__container {
  display: flex;
  align-items: center;
}

.main-header__button {
  margin-left: 40px;
  width: 218px;
  height: 44px;
  font-style: normal;
  font-weight: normal;
  font-size: 18px;
  line-height: 24px;
  transition: opacity 0.3s;
}

.main-header__button:hover {
  opacity: 0.9;
}

.main-header__mobile-icon {
  display: none;
}

@media screen and (max-width: 1350px) {
  .main-header {
    padding: 18px 50px 18px;
  }

  .main-header__logo {
    line-height: 18px;
  }

  .main-header__button {
    width: 211px;
    height: 42px;
  }
}

@media screen and (max-width: 1250px) {
  .main-header__button {
    margin-left: 30px;
    font-size: 15px;
    line-height: 18px;
    width: 201px;
    height: 38px;
  }

  .main-header {
    min-height: 36px;
  }
}

@media screen and (max-width: 1000px) {
  .main-header {
    min-height: 28px;
    border-top: 1px solid #efefef;
  }

  .main-header__logo {
    width: 216px;
    font-size: 12px;
    line-height: 14px;
  }

  .main-header__container {
    display: none;
  }

  .main-header__mobile-icon {
    display: block;
  }
}

@media screen and (max-width: 700px) {
  .main-header {
    padding: 18px 15px 18px;
  }
}
</style>
