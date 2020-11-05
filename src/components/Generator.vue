<template>
  <div class="container">
    <div class="text">
      <h1 class="quote">{{ quote }}</h1>
      <h2 class="author" v-if="author != null">- {{ author }}</h2>
    </div>
    <div class="icons">
      <a href="https://github.com/Hougesen"> <i class="fab fa-github-square fa-2x"></i> </a>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Generator',
    data() {
      return {
        quote: '',
        author: '',
      };
    },

    beforeMount() {
      this.fetchQuote();
      this.fetchBackground();
    },

    methods: {
      fetchQuote: function() {
        const baseURI = 'https://type.fit/api/quotes';
        this.$http.get(baseURI).then((result) => {
          let randomNum = Math.floor(Math.random() * Object.keys(result.data).length);
          this.quote = result.data[randomNum].text;
          this.author = result.data[randomNum].author;
        });
      },

      fetchBackground() {
        let wWidth = window.innerWidth;
        let wHeight = window.innerHeight;
        document.body.style.backgroundImage = `linear-gradient( rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5) ), url("https://picsum.photos/${wWidth}/${wHeight}")`;
      },
    },
  };
</script>

<style scoped>
  .text {
    text-align: center;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: rgb(255, 255, 255);
  }

  .quote {
    font-size: clamp(1.75rem, 3vw, 2.1rem);
  }

  .author {
    font-style: italic;
    font-size: clamp(1.295rem, 2.1vw, 1.47rem);
  }

  @import 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.1/css/all.min.css';
  .icons {
    position: absolute;
    text-align: center;
    bottom: 0;
    left: 0;
    right: 0;
  }

  .fa-github-square {
    mix-blend-mode: difference;
    color: rgb(255, 255, 255);
  }
</style>
