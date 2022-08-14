<template>
  <div>
    <div class="tweet_container"></div>
    <button class="button_one">page layout</button>
  </div>
</template>

<script>
export default {                                                          
  mounted() {                                                             // when everything is loaded on the page
    this.show_tweets();                                                   // display this(current component) show_tweets

    let button_one = document.querySelector(`.button_one`);               // gets the first button_one (class, button on page) sets to variable button_one
    button_one.addEventListener(`click`, this.page_orientation);          // when button_one is clicked it will call the page orientation component
  },

  methods: {
    page_orientation() {                                                  // function named page orientation
      let tweet_container = document.querySelector(`.tweet_container`);   // gets the first tweet_container (class) and sets it as the variable tweet_container
      if (tweet_container[`style`][`gridAutoFlow`] === `row`) {           // conditional that checks to see if tweet_container is equal to row
        tweet_container[`style`][`gridAutoFlow`] = `column`;              // if its = to row it will set tweet_container to coloumn
      } else {
        tweet_container[`style`][`gridAutoFlow`] = `row`;                 // otherwise it will set the tweet_container to row
      }
    },

    show_tweets: function () {                                            // show_tweets function
      for (let i = 0; i < this.tweets.length; i++) {                      // loops through the tweets if i is less than the tweets length it will incrament by 1
        document.querySelector(`.tweet_container`).insertAdjacentHTML(    // gets the tweet_container from the page (class) and injects html from user i
          `afterbegin`,
          `<section>
          <h1>user:${this.user[i]}</h1>
          <h2>Tweet:${this.tweets[i]}</h2>
          <h4>Date Created:${this.created[i]}</h4>
          </section>`
        );
      }
    },
  },

  data() {                                                                // object containing different keys and values [array]
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
}
</style>