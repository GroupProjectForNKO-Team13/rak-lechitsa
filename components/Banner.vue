<template>
  <section class="banner">
    <div class="banner__background">
      <h2 class="banner__text">
        {{ title }}
        <span class="banner__hashtag"> {{ blockBanner.hashtag }}</span>
      </h2>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    title: String,
  },
  computed: {
    blockArr() {
      return this.$store.getters['blocks/getBlockArr'];
    },
    blockBanner() {
      return this.blockArr.find(el => el.block === 'note-1');
    },
  },
};
</script>

<style scoped>
.banner {
  padding: 0 60px;
}

.banner__background {
  padding: 20px 20px;
  margin: 0 auto;
  max-width: 1320px;
  background-color: #613a93;
}

.banner__text {
  font-style: normal;
  font-weight: normal;
  font-size: 30px;
  line-height: 46px;
  text-align: center;
  color: #ffffff;
  text-transform: uppercase;
}

.banner__hashtag {
  font-weight: bold;
  font-size: 40px;
  line-height: 1;
}

@media (max-width: 1300px) {
  .banner {
    padding: 0 50px;
  }

  .banner__text {
    font-size: 28px;
    line-height: 46px;
  }

  .banner__hashtag {
    font-size: 38px;
  }
}

@media (max-width: 1200px) {
  .banner__text {
    font-size: 24px;
    line-height: 40px;
  }

  .banner__hashtag {
    font-size: 34px;
  }
}

@media (max-width: 800px) {
  .banner__background {
    padding: 12px 65px;
  }

  .banner {
    padding: 0 40px;
  }

  .banner__text {
    font-size: 22px;
    line-height: 36px;
  }

  .banner__hashtag {
    font-size: 32px;
  }
}

@media (max-width: 600px) {
  .banner__background {
    padding: 10px 20px;
  }

  .banner {
    padding: 0 15px;
  }

  .banner__text {
    font-size: 16px;
    line-height: 18px;
    max-width: 220px;
    margin: 0 auto;
  }

  .banner__hashtag {
    font-size: 22px;
  }
}
</style>
