<template>
  <div :class="`countdown ${mode}`">
    <div>
      <div class="item">{{ day }}</div>
      <p>days</p>
    </div>
    <div>
      <div class="item">{{ hour }}</div>
      <p>hours</p>
    </div>
    <div v-if="showMinute">
      <div class="item">{{ minute }}</div>
      <p>minutes</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Countdown",
  props: {
    deadline: Date,
    mode: String,
    showMinute: {
      type: Boolean,
      default: true
    }
  },
  data() {
    return {
      now: new Date(),
      interval: null
    }
  },
  created() {
    this.interval = setInterval(() => {
      this.now = new Date()
    }, 1000)
  },
  methods: {
    twoDigits(v) {
      if (v < 10)
        return '0' + v
      return v
    }
  },
  computed: {
    diff() {
      if (this.deadline <= this.now) return 0
      return Math.trunc((this.deadline - this.now) / 1000)
    },
    minute() {
      return this.twoDigits(Math.trunc(this.diff / 60) % 60)
    },
    hour() {
      return this.twoDigits(Math.trunc(this.diff / 60 / 60) % 24)
    },
    day() {
      return this.twoDigits(Math.trunc(this.diff / 60 / 60 / 24))
    }
  },
  beforeUnmount() {
    clearInterval(this.interval)
  }
}
</script>

<style scoped lang="scss">
.countdown {
  display: flex;
  color: #efefef;
  font-weight: 500;

  & > div {
    padding: 0 8px;
  }

  .item {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  p {
    margin: 0;
    text-align: center;
    font-size: 12px;
  }

  &.horizontal > div {
    display: flex;
    align-items: center;
    padding: 0 2px;

    p {
      font-size: inherit;
    }
  }
}
</style>