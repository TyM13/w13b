<template>
  <div>
    <div class="tweet_container"></div>
    <button class="button_one">page layout</button>
  </div>
</template>

<script>


export default {




  mounted() {
    this.show_tweets();

let button_one = document.querySelector(`.button_one`)
button_one.addEvenListener(`click`, this.page_orientation)
  
  },

  methods: {

//     page_orientation() {
  
// [`target`][`display`][`grid-auto-flow`] 

//     },

    show_tweets: function () {
      for (let i = 0; i < this.tweets.length; i++) {
        document.querySelector(`.tweet_container`).insertAdjacentHTML(
          `afterbegin`,
          `<h3>Tweet:${this.tweets[i]}</h3>
          <h1>user:${this.user[i]}</h1>
          <h1>Date Created:${this.created[i]}</h1>`
        );
      }
    },
  },
  
  data() {
    return {
      tweets: [`randomtweet1`, `randomtweet2`, `randomtweet3`],
      user: [`Tyler`, `David`, `Sam`],
      created: [2022, 2014, 2019],
    };
  },

  name: "tweeted-tweets",
};
</script>

<style scoped>
h1 {
  display: grid;
  grid-auto-flow: column;
}
</style>