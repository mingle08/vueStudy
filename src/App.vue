<!--
<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>
-->

<template>
  <div id="app">
    <h1>服务端数据为：{{serverData}}</h1>
    <img src="./assets/logo.png" @click="getData()">    
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      serverData: 'data from fake server'
    }
  },
  mounted: function () {
    this.getData()
  },
  methods: {
    getData () {
      console.log('-------getData')
      var that = this
 //192.168.1.101为后端IP地址     this.$http.get('http://localhost:8082/vue-springmvc/hello/getperson/33333')
                .then(function (response) {
                  console.log(response)
                  console.log(this)
                  that.serverData = response.data
                })
                .catch(function (error) {
                  console.log(error)
                })
    }
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
