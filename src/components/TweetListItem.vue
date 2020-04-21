<template lang="html">
<div>
  <p>{{tweet.name}}</p>
  <p>{{tweet.handle}}</p>
  <img :src="tweet.img " width='100' height= '100'>
  <p>{{tweet.tweet}}</p>
  <p>{{tweet.likes}}</p>
</div>
</template>

<script>
export default {
  name: 'tweet-list-item',
  props: ['tweet']
}

</script>

<style lang="css" scoped>

</style>
