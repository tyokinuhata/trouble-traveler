<template>
  <div>
    <h1 class="title">Trouble Traveler</h1>
    <h2 class="subtitle">Decide the next travel destination fastest.</h2>
    <div class="content">
      <div class="imgWrapper">
        <img :src="'./static/preferences/' + travel.image + '.png'" alt="" class="img">
      </div>
      <div class="info">
        <div>
          <span class="preference">{{ travel.preference }}</span>
          <span>{{ travel.region }}</span>
        </div>
        <div>{{ travel.description }}</div>
      </div>
    </div>
    <div class="buttonWrapper">
      <div class="button" @click="gacha()">ガチャる</div>
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
          preference: '？？？',
          region: '？？？',
          description: '？？？',
          image: 'nidukuri'
        }
      }
    },
    methods: {
      gacha() {
        let id, sec = 0

        const getRandom = () => {
          id = Math.floor(Math.random() * 46 + 1)
          this.travel.preference = this.preferences.result[id - 1].preference
          this.travel.region = this.preferences.result[id - 1].region
          this.travel.description = this.preferences.result[id - 1].description
          this.travel.image = this.preferences.result[id - 1].image
        }

        setTimeout(function roop() {

          getRandom()
          sec += 2

          if (sec < 100) {
            setTimeout(roop, sec)
          }
        }, sec)
      }
    }
  }
</script>

<style lang="scss" scoped>
  .title {
    margin-bottom: 5px;
    text-align: center;
    font-family: 'Monaco', courier, monospace;

    @media screen and (max-width: 500px) {
      margin-top: 5px;
    }
  }
  .subtitle {
    margin-top: 5px;
    text-align: center;
    font-family: 'Monaco', courier, monospace;
    font-size: 16px;
  }
  .content {
    width: 100%;
    height: 350px;
    text-align: center;
  }
  .imgWrapper {
    position: relative;
    width: 200px;
    height: 250px;
    margin: 0 auto;
    border: 10px solid #ffc0cb;
    border-radius: 10px;
    vertical-align: middle;
  }
  .img {
    position: absolute;
    width: 100%;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: auto;
  }
  .info {
    margin-top: 10px;
  }
  .preference {
    font-size: 24px;
  }
  .buttonWrapper {
    margin-top: 10px;

    @media screen and (max-width: 500px) {
      margin-top: 0;
    }
  }
  .button {
    width: 250px;
    height: 230px;
    margin: 0 auto;
    border-radius: 50%;
    box-shadow: 0 15px 0 #942343;
    background: #dc143c;
    text-align: center;
    line-height: 230px;
    letter-spacing: 3px;
    font-size: 32px;
    font-weight: bold;
    color: #fff;
    cursor: pointer;

    &:active {
      transform: translateY(15px);
      box-shadow: none;
    }

    @media screen and (max-width: 500px) {
      height: 60px;
      border-radius: 5px;
      line-height: 60px;
    }
  }
</style>
