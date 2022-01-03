<template>
  <div class="game">
    <div class="game-image">
      <img alt :src="image"/>
    </div>
    <div class="game-detail">
      <div class="game-title">
        <div class="text">
          <h1>{{ name }}</h1>
          <p>#{{details}}</p>
        </div>
        <div class="price">$ {{price ? price.toFixed(2) : '0.00'}}</div>
      </div>
      <div class="game-desc">
        {{description}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Game",
  props: {
    name: String,
    description: String,
    thumbnailImageUrl: String,
    details: String,
    price: Number,
  },
  computed: {
    image() {
      if (this.thumbnailImageUrl) {
        return this.thumbnailImageUrl
      }
      return 'https://picsum.photos/600/300'
    }
  }
}
</script>

<style scoped lang="scss">
  .game {
    border-radius: 16px;
    background: #212c43;
    height: 100%;

    &-image {
      border-radius: inherit;

      img {
        border-radius: inherit;
        width: 300px;
      }
    }

    &-detail {
      padding: 0 16px 16px;
    }

    &-title {
      display: flex;
      align-items: center;
      justify-content: space-between;

      .text {

        h1 {
          font-size: 20px;
          line-height: 28px;
          margin: 0;
          max-width: 120px;
          word-break: break-word;
        }

        p {
          font-weight: 500;
          color: #9e65ec;
          margin: 4px 0;
        }
      }

      .price {
        background: #596274;
        padding: 4px 8px;
        border-radius: 16px;
      }
    }

    &-desc {
      word-break: break-word;
      max-width: calc(300px - 32px);
    }
  }
</style>