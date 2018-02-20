<template>
  <div class="pages">
    <h1>Trouble Traveler</h1>
    <button type="button" @click="gacha()">ガチャる</button>
    <div>
      <div>{{ travel.preference }}</div>
      <div>{{ travel.region }}</div>
    </div>
  </div>
</template>

<script>
  import preferences from './preferences.json'

  export default {
    data() {
      return {
        preferences: preferences,
        travel: {
          preference: '',
          region: ''
        }
      }
    },
    methods: {
      gacha() {
        const id = Math.floor(Math.random() * 46 + 1)
        this.travel.preference = this.preferences.result[id].preference
        this.travel.region = this.preferences.result[id].region
      }
    }
  }
</script>
