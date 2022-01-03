<template>
  <div id="app">
    <Header/>
    <Search/>
    <Banner v-bind="banner" :video="video"/>
    <div class="delimiter">
      <div v-for="i in 5" :key="i" :class="`${i === 3 ? 'selected' : ''}`"></div>
    </div>
    <section>
      <h1 class="title">Features jams</h1>
      <div class="list">
        <div v-for="(jam, i) in jams" :key="i" class="list-item">
          <Jam v-bind="jam"/>
        </div>
      </div>
      <div class="btn">View More</div>
    </section>
    <section>
      <h1 class="title">Features games</h1>
      <div class="list">
        <div v-for="(game, i) in games" :key="i" class="list-item">
          <Game v-bind="game"/>
        </div>
      </div>
      <div class="btn">View More</div>
    </section>
  </div>
</template>

<script>
import Header from "./components/Header";
import data from './assets/frontend_test_homepage_data.json'
import Search from "./components/Search";
import Jam from "./components/Jam";
import Game from "./components/Game";
import Banner from "./components/Banner";

export default {
  name: 'App',
  components: {
    Banner,
    Game,
    Jam,
    Search,
    Header,
  },
  data() {
    return {
      video: data.videos[0],
      banner: data.bigFeaturedJam,
      jams: data.jams,
      games: data.games[0].data,
    }
  },
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: whitesmoke;
  background: #374460;
  padding-bottom: 60px;

  section {
    width: 960px;
    margin: auto;
  }

  .title {
    font-size: 20px;
    line-height: 28px;
    text-transform: uppercase;
    padding: 16px 32px;
  }

  .delimiter {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 16px;

    div {
      width: 8px;
      height: 8px;
      background: #596274;
      border-radius: 8px;
      margin: 0 8px;

      &.selected {
        background: #eeeeee;
      }
    }
  }

  .list {
    max-width: 100%;
    overflow: auto;
    display: flex;
    align-items: stretch;
    padding-bottom: 4px;

    &-item:not(:last-child) {
      margin-right: 30px;
    }

    &::-webkit-scrollbar {
      width: 6px;
      height: 6px;
      border-radius: 8px;
      background: #596274;
      margin-top: 2px;
    }

    &::-webkit-scrollbar-thumb {
      border-radius: 8px;
      background: #1e293e;
    }
  }

  .btn {
    margin: 12px 0 12px auto;
    border: 1px solid white;
    border-radius: 16px;
    width: fit-content;
    padding: 4px 8px;
    cursor: pointer;
  }

}
</style>
