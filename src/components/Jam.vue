<template>
  <div class="jam">
    <div class="jam-image">
      <img alt :src="thumbnailImageUrl"/>
    </div>
    <div class="jam-detail">
      <h1 class="jam-title">{{ name }}</h1>
      <h2 class="jam-subtitle">Hosted by {{ host }}</h2>
      <div class="jam-date">
        {{ deadlineText }}
        <countdown :deadline="deadline" mode="horizontal" :show-minute="false"/>
      </div>
      <progress class="jam-progress" :value="joinedCount" :max="submissionCount"></progress>
      <div class="jam-info">
        {{ joinedCount }} Joined {{ submissionCount }} Submissions
      </div>
    </div>
  </div>
</template>

<script>
import Countdown from "./Countdown";
export default {
  name: "Jam",
  components: {Countdown},
  props: {
    name: String,
    thumbnailImageUrl: String,
    startTime: Number,
    endTime: Number,
    resultTime: Number,
    hostProfiles: Array,
    submissionCount: Number,
    joinedCount: Number
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
  .jam {
    border-radius: 16px;
    background: #212c43;

    &-image {
      border-radius: inherit;

      img {
        border-radius: inherit;
        max-width: 300px;
      }
    }

    &-detail {
      padding: 0 16px 16px;
    }

    &-title {
      font-size: 20px;
      line-height: 24px;
      text-transform: uppercase;
      margin: 0;
    }

    &-subtitle {
      font-size: 16px;
      line-height: 24px;
      color: #9e65ec;
      font-style: italic;
      font-weight: 500;
      margin-bottom: 12px;
    }

    progress {
      appearance: none;
      display: block;
      width: 100%;
      height: 12px;
      color: #9e65ec;
      border-radius: 12px;
      margin: 4px 0;

      &::-webkit-progress-bar {
        background-color: #374460;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.25) inset;
        border-radius: 6px;
      }

      &::-webkit-progress-value {
        background: linear-gradient(to right, #5357f7, #9e65ec);
        border-radius: 6px;
      }

      &::-moz-progress-bar {
        background: linear-gradient(to right, #5357f7, #9e65ec);
        border-radius: 6px;
      }
    }

    &-date {
      display: flex;
      align-items: center;
      font-style: italic;
      color: #eeeeee;
    }

    &-info {
      font-style: italic;
      font-size: 14px;
      color: #eeeeee;
    }
  }
</style>