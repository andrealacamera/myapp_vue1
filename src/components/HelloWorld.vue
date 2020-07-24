<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="teiga"> 
      <p>{{t1}}</p>
    
    </div>

  </div>
</template>

<script>
export default {
  name: 'MioTest',
  props: {
    msg: String, 
    t1: String
  },
  data() {
    return {
      p : 'ciao'}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
.teiga {
  color: #42b983;
  }
</style>
