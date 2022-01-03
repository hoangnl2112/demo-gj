<template>
  <div class="banner">
    <div class="banner-video">
      <video muted autoplay loop :src="video" :poster="thumbnailImageUrl"/>
    </div>
    <div class="banner-detail">
      <h1 class="banner-title">
        {{ name }}
      </h1>
      <p class="banner-subtitle">
        Hosted by {{ host }}
      </p>
      <div class="banner-info">
        <div class="clock">
          <div>{{ deadlineText }}</div>
          <countdown :deadline="deadline"/>
        </div>
        <div class="text">
          <div>
            <p>{{ joinedCount }}</p>
            <p>Joined</p>
          </div>
          <div>
            <p>{{ submissionCount }}</p>
            <p>Submissions</p>
          </div>
        </div>
      </div>
      <div class="banner-button">
        Join Now!
      </div>
    </div>
  </div>
</template>

<script>
import Countdown from "@/components/Countdown";
export default {
  name: "Banner",
  props: {
    name: String,
    thumbnailImageUrl: String,
    startTime: Number,
    endTime: Number,
    resultTime: Number,
    hostProfiles: Array,
    submissionCount: Number,
    joinedCount: Number,
    video: String,
  },
  components: {
    Countdown
  },
  data() {
    return {
      now: new Date()
    }
  },
  computed: {
    host() {
      if(this.hostProfiles.length) {
        return this.hostProfiles.map(h => h.username).join(', ')
      }
      return ''
    },
    deadlineText() {
      return new Date(this.startTime) > this.now
          ? 'Starts In'
          : new Date(this.endTime) > this.now
              ? 'Ends In'
              : 'Results In'
    },
    deadline() {
      return new Date(this.startTime) > this.now
          ? new Date(this.startTime)
          : new Date(this.endTime) > this.now
              ? new Date(this.endTime)
              : new Date(this.resultTime)
    }
  }
}
</script>

<style scoped lang="scss">
  .banner {
    display: flex;
    align-items: stretch;

    &-video {
      flex: 0 0 50%;

      video {
        width: 100%;
        display: block;
      }
    }

    &-detail {
      padding: 40px 100px;
      flex: 1;
      background: #1e293e;
      display: flex;
      flex-direction: column;
      justify-items: center;
    }

    &-title {
      font-size: 36px;
      line-height: 44px;
      margin: 0;
    }

    &-subtitle {
      font-size: 16px;
      line-height: 24px;
      color: #9e65ec;
      font-style: italic;
      font-weight: 500;
    }

    &-info {
      margin: 16px 0;
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      font-size: 20px;
      color: #eee;

      .clock > div:first-child {
        margin-bottom: 12px;
      }

      .text {
        display: flex;
        align-items: center;
        text-align: center;

        div {
          margin: 0 8px;

          p:last-child {
            font-size: 12px;
          }
        }
      }
    }

    &-button {
      color: white;
      border-radius: 32px;
      background: linear-gradient(to right, #5357f7, #9e65ec);
      padding: 8px 12px;
      text-transform: uppercase;
      width: 120px;
      margin: 24px auto;
      text-align: center;
      cursor: pointer;
    }
  }
</style>