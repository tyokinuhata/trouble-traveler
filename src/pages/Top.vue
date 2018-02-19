<template>
  <div class="pages">
    <h1>Trouble Traveler</h1>
    <button type="button" @click="gacha()">ガチャる</button>
    <div>{{ travel }}</div>
  </div>
</template>

<script>
  import data from './data.json'

  export default {
    data() {
      return {
        data: data,
        travel: ''
      }
    },
    methods: {
      gacha() {
        const id = Math.floor(Math.random() * 46 + 1)
        this.travel = this.data.result[id].preference
      }
    }
  }
</script>
