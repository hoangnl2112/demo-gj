<template>
  <div class="search">
    <div class="input">
      <input placeholder="Search" v-model="model">
      <div class="arrow">
        <svg width="20" height="10" viewBox="0 0 20 10" fill="white" xmlns="http://www.w3.org/2000/svg">
          <path d="M0.749681 3.89812H12.9152C14.2815 3.89812 14.964 2.24472 13.9956 1.28098C13.7021 0.98892 13.701 0.514287 13.9931 0.220841C14.2851 -0.0726426 14.7598 -0.0737293 15.0532 0.218292L18.9702 4.11641C18.9705 4.11664 18.9707 4.1169 18.9709 4.11712C19.2636 4.40918 19.2645 4.88535 18.971 5.17839C18.9707 5.17861 18.9705 5.17887 18.9703 5.1791L15.0533 9.07722C14.7599 9.3692 14.2852 9.36819 13.9931 9.07467C13.7011 8.78122 13.7022 8.30659 13.9956 8.01453C14.9641 7.05078 14.2815 5.39739 12.9153 5.39739H0.749681C0.335657 5.39739 4.3869e-05 5.06178 4.3869e-05 4.64775C4.3869e-05 4.23373 0.335657 3.89812 0.749681 3.89812Z" fill="white"/>
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Search",
  props: {
    value: String
  },
  computed: {
    model: {
      get() {
        return this.value
      },
      set(v) {
        this.$emit('input', v)
      }
    }
  }
}
</script>

<style scoped lang="scss">
  .search {
    padding: 24px;
    display: flex;
    align-items: center;
    justify-content: flex-end;

    .input {
      display: flex;
      border-radius: 32px;
      background: #1e293e;
      padding: 8px;

      input {
        border: none;
        outline: none;
        padding: 4px;
        font-size: 16px;
        line-height: 24px;
        background: transparent;
      }

      .arrow {
        width: 32px;
        height: 32px;
        display: flex;
        align-items: center;
        justify-content: center;
        background: #9e65ec;
        border-radius: 50%;
        cursor: pointer;
      }
    }
  }
</style>