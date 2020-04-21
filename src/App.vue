<template lang="html">
  <div>
    <h1>Twitter</h1>
    <h2>Total Likes: {{totalLikes}}</h2>
    <form v-on:submit.prevent="saveUser">
        <h3>Add A New User</h3>
        <input placeholder="Name" type="text" v-model="newUser.name" />
        <input placeholder="Handle" type="text" v-model="newUser.handle"/>
        <input placeholder="Avatar URL" type="text" v-model="newUser.img"/>
        <input placeholder="Tweet" type="text" v-model="newUser.tweet"/>
        <input placeholder="Likes" type="number" v-model="newUser.likes"/>
        <input type="submit" value="Add User"/>
    </form>
      <ul>
        <tweet-list-item v-for="(tweet, index) in tweets" :key="index" :tweet="tweet"></tweet-list-item>
      </ul>
  </div>
</template>

<script>

import TweetListItem from './components/TweetListItem.vue';

export default {
  name: 'app',
  data() {
    return {
      tweets:[
        {
          id: 1,
          name: 'James',
          handle: '@jokerjames',
          img: 'https://semantic-ui.com/images/avatar2/large/matthew.png',
          tweet: "If you don't succeed, dust yourself off and try again.",
          likes: 10,
        },
        {
          id: 2,
          name: 'Fatima',
          handle: '@fantasticfatima',
          img: 'https://semantic-ui.com/images/avatar2/large/molly.png',
          tweet: 'Better late than never but never late is better.',
          likes: 12,
        },
        {
          id: 3,
          name: 'Xin',
          handle: '@xeroxin',
          img: 'https://semantic-ui.com/images/avatar2/large/elyse.png',
          tweet: 'Beauty in the struggle, ugliness in the success.',
          likes: 18,
        }
      ],
      newUser: {
        name: "",
        handle: "",
        img: "",
        tweet: "",
        likes: 0,
      },

    };
  },
  components: {
    'tweet-list-item': TweetListItem
  },
  computed: {
    totalLikes: function(){
      return this.tweets.reduce((total, tweet) => tweet.likes, 0);
    },
  },
  methods: {
    saveUser: function(){
        this.tweets.unshift(this.newUser);

        this.newUser = {
          name: "",
          handle: "",
          img: "",
          tweet: "",
          likes: 0,
        };
      }
  }

}
</script>

<style lang="css" scoped>
header {
  background: #eee;
  padding: 10px 20px;
  font: Helvetica Neue;
  color: black;
}

form, #saveUser {
  background: #eee;
  padding: 10px 20px 20px 20px;
  margin-top: 40px;
}

section {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}

.tweets {
  background: #b2ebf2;
  padding: 10px 20px;
  margin: 20px 0;
  width: 20%;
}
</style>
