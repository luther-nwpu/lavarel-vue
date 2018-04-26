<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>

    <h2>Ecosystem</h2>
      {{name}}
    <button @click="fun">点击改变msg</button>
    <br>
    msg: {{msg}}
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'

export default {
  name: 'HelloWorld',
  data () {
    return {
      name: 'sada',
    }
  },
  created(){
    console.log(1323)
    fetch('/user/hello', {
      method: 'GET',
      headers: {
        'Content-Type': 'application/json'
      },
    }).then(function(response) {
      return response.json()
    }).then(function(result){
      console.log(result)
    }).catch(function(err){
      console.log(err)
    })
  },
  computed: {...mapGetters(['msg'])},  //对应getters.技术中的msg
  methods: {...mapActions(['fun'])}   //对应 Actions中fun方法
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
