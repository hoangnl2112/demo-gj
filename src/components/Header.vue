<template>
  <header>
    <ul>
      <li>
        <a href="#">
          <img alt src="../assets/gamejam_logo.svg"/>
        </a>
      </li>
      <li>
        <a href="#">Browse games</a>
      </li>
    </ul>
    <ul>
      <li>
        <a href="#">Upload Game</a>
      </li>
      <li>
        <a href="#">Community</a>
      </li>
      <li>
        <a href="#">Support</a>
      </li>
    </ul>
    <ul>
      <li>
        <a href="#">Sign up</a>
      </li>
      <li>
        <a href="#">Log in</a>
      </li>
    </ul>
  </header>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scoped lang="scss">
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 24px;
  background: #1e293e;

  img {
    width: 150px;
  }

  ul {
    display: flex;
    align-items: center;
    justify-items: center;
    margin: 0;
    padding: 0;

    li {
      a {
        color: white;
        padding: 0 8px;
        text-decoration: none;
      }
    }
  }
}
</style>