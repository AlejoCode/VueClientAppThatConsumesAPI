<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
            <div class="mt-5">

    <p>
      First consumming the /list endpoint for listing the playlists 
    </p>
        </div>

  <div>
    
    <vue-json-pretty
      :data="{ info  }"
    >
    </vue-json-pretty>
        <div class="mt-5 ">

        <p>
      The same rendered as a table with <a href="https://www.npmjs.com/package/vue-json-pretty" target="_blank" rel="noopener">vue-json-pretty
    </a> npm Package
    </p>
        </div>

    <div class="pl-5 pr-5">
      <b-table striped hover :items=" info "></b-table>
    </div>
  </div>

    <footer class="footer navbar-fixed-bottom mt-5 mb-5">
      <div class="container">
        <span class="text-muted">&copy;DoneBy</span>
        <a class="ml-2" href="https://github.com/AlejoCode">https://github.com/AlejoCode</a>
      </div>
    </footer>
  </div>
</template>

<script>
import axios from 'axios'
import VueJsonPretty from 'vue-json-pretty'


export default {
  name: 'HelloWorld',

  data () {
    return {
      info: null,
      selected: null
    }
  },
  mounted () {
    axios
      .get('https://alejo-code-inalambria-api.herokuapp.com/playLists/list')
      .then(response => (this.info = response.data.docs))
  },
  props: {
    msg: String,

  },
  components: {
    VueJsonPretty
  },

}
// this.info.forEach(x => { 
//   return {
//       render (createElement) {
//         return createElement('h1', x.name);
//       }
//     };
// });

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

</style>
