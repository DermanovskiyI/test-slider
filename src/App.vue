<template>
  <router-view></router-view>
</template>

<style lang="scss">

html, body {
    height: 100%;
}
body {
    -webkit-font-smoothing: antialiased;
    -moz-osx-webkit-font-smoothing: grayscale;
    margin: 0;
}
#app {
  height: 100%;
}
.wrapper {
    min-width: 0;
    height: 100%;
    width: 100%;
}

.container {
    width: auto;
    max-width: 918px;
    height: 100%;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

* {
    box-sizing: border-box;
}

ul {
    padding: 0;
    margin: 0;

    li {
        list-style-type: none;
    }
}

h1, h2, h3, h4, h5, h6 {
    margin: 0;
    font-weight: normal;
}

p {
    margin: 0;
}
a {
  color: black;
  text-decoration: none;
}
img {
  max-width: 100%;
}

</style>
