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

    let button_one = document.querySelector(`.button_one`);
    button_one.addEventListener(`click`, this.page_orientation);
  },

  methods: {
    page_orientation() {                                                          //still don't know how to write syntax proplerly
      let tweet_container = document.getElementsByClassName(`tweet_container`);
      if ([`style`][`grid-auto-flow: row` === true]) {
        tweet_container[`style`][`grid-template-columns`] = `1fr 1fr 1fr`;             
      } else if ([`style`][`grid-template-columns: 1fr 1fr 1fr;` === true]) {
        tweet_container[`style`][`grid-auto-flow: row`];
      }
    },

    show_tweets: function () {
      for (let i = 0; i < this.tweets.length; i++) {
        document.querySelector(`.tweet_container`).insertAdjacentHTML(
          `afterbegin`,
          `<h1>user:${this.user[i]}</h1>
          <h2>Tweet:${this.tweets[i]}</h2>
          <h4>Date Created:${this.created[i]}</h4>`
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
.tweet_container {
  display: grid;
  grid-auto-flow: row;
  /* grid-template-columns: 1fr 1fr 1fr;   for reference*/
}
</style>