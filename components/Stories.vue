<template>
  <section class="stories">
    <stories-content class="stories__content">
      <h3 class="stories__heading">{{ blockStories.title }}</h3>
      <stories-grid
        class="stories__list"
        :relevantStories="allStories"
        :start="0"
        :limit="widthLimit"
      />
      <nuxt-link to="/stories" class="stories__page">Больше статей</nuxt-link>
    </stories-content>
  </section>
</template>

<script>
import Content from '@/components/ui/Content';
import StoriesGrid from '@/components/StoriesGrid';
export default {
  components: {
    'stories-content': Content,
    'stories-grid': StoriesGrid,
  },
  computed: {
    blockArr() {
      return this.$store.getters['blocks/getBlockArr'];
    },
    blockStories() {
      return this.blockArr.find(el => el.block === 'stories');
    },
    allStories() {
      return this.$store.getters['stories/getAllStories'];
    },
    widthLimit() {
      this.limit = 8;
      if (window.innerWidth <= 1000) {
        this.limit = 9;
      }
      if (window.innerWidth <= 700) {
        this.limit = 6;
      }
      return this.limit;
    },
  },
};
</script>

<style scoped>
.stories__list {
  display: grid;
  grid-template-columns: repeat(auto-fill, 300px);
  grid-gap: 70px 40px;
  padding: 0;
  list-style-type: none;
}
.stories__heading {
  margin: 100px 0 70px;
  padding: 0;
  max-width: 410px;
  font-weight: 600;
  font-size: 32px;
  line-height: 36px;
  color: #000;
}
.stories__page {
  margin: 70px auto 100px;
  max-width: 1320px;
  min-height: 82px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
  font-size: 16px;
  line-height: 20px;
  color: #000;
  background-color: #fbfbfb;
  transition: background-color 0.3s;
}
.stories__page:hover {
  background-color: #f8f8f8;
}
.stories__box {
  display: flex;
  width: 100%;
  justify-content: space-between;
}
.stories__link {
  text-decoration: none;
}

@media screen and (max-width: 1350px) {
  .stories__heading {
    margin: 90px 0 60px;
    font-size: 28px;
    line-height: 32px;
  }

  .stories__page {
    margin-bottom: 90px;
    margin-top: 60px;
  }

  .stories__list {
    grid-template-columns: repeat(auto-fill, 265px);
    grid-gap: 60px 40px;
  }
}

@media screen and (max-width: 1250px) {
  .stories__list {
    grid-template-columns: repeat(auto-fill, 208px);
    grid-gap: 46px 30px;
  }

  .stories__heading {
    margin: 80px 0 46px;
    font-size: 24px;
    line-height: 28px;
    max-width: 288px;
  }

  .stories__page {
    margin-bottom: 80px;
    margin-top: 46px;
    font-size: 13px;
    line-height: 20px;
  }
}

@media screen and (max-width: 1000px) {
  .stories__list {
    grid-template-columns: repeat(auto-fill, 216px);
    grid-gap: 40px 20px;
  }

  .stories__heading {
    margin: 80px auto 60px;
    text-align: center;
  }

  .stories__page {
    margin-bottom: 80px;
    margin-top: 40px;
  }
}

@media screen and (max-width: 700px) {
  .stories__page {
    margin-bottom: 50px;
  }

  .stories__heading {
    margin: 50px auto 40px;
    font-size: 18px;
    line-height: 21px;
    text-align: inherit;
  }

  .stories__list {
    grid-template-columns: repeat(auto-fill, 290px);
    grid-gap: 30px 20px;
  }
}
</style>
