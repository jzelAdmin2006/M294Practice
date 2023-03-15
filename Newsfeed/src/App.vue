<script setup>
import { ref } from 'vue'
import NewsfeedItem from './NewsfeedItem.vue'

const items = ref([
  {
    id: 1,
    title: 'Lorem ipsum dolor sit amet, consetetur sadipscing elitr',
    teaser: 'At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.',
    numberOfWords: 512,
    image: 'https://placekitten.com/200/200',
  },
  {
    id: 2,
    title: 'At vero eos et accusam et justo duo',
    teaser: 'Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren.',
    numberOfWords: 1723,
    image: 'https://placekitten.com/200/200',
  },
  {
    id: 3,
    title: 'Consetetur sadipscing elitr, sed diam nonumy eirmod tempor ',
    teaser: 'labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.',
    numberOfWords: 821,
    image: 'https://placekitten.com/200/200',
  },
])
</script>

<template>
  <h1>Newsfeed</h1>
  <div class="box">
    <div class="newsfeed">
      <NewsfeedItem v-for="item in items" :key="item.id" :title="item.title" :teaser="item.teaser" :image="item.image"
        :numberOfWords="item.numberOfWords" />
    </div>
  </div>
</template>

<style>
body {
  background: #0f172a;
  color: #fff;
  margin: 4rem auto;
  max-width: 620px;
  padding: 20px;
}

.box {
  box-shadow: inset 0 1px 0 0 hsla(0, 0%, 100%, .05);
  background: rgb(30 41 59/1);
  border-radius: 5px;
  overflow: hidden;
}

.newsfeed {
  margin: 0;
  padding: 0;
}
</style>