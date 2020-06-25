<template>
  <div>
    <appHeader/>
    <Nuxt />
    <appFooter/>
  </div>
</template>

<script>

import appHeader from '../components/appHeader'
import appFooter from '../components/appFooter'


export default {
  components:{
    appHeader,
    appFooter
  }
}
</script>

<style>
html {
  font-family: 'Lato', sans-serif;
  /* font-size: 16px;
  word-spacing: 1px; */
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}
body{
  margin: 0;
}
h1,h2,h3{
  font-family: 'Paytone One',sans-serif;
  font-weight: 400;
  margin: 0.25em 0;
}
h1{
  font-size: 3.052rem;
}
h2{
  font-size: 2.441rem;
}
h3{
  font-size: 1.953rem;
}
h4{
  font-size: 1.563rem;
  margin: 0;
}
p{
  font-size: 1.25rem;
  margin: 0;
}

</style>
