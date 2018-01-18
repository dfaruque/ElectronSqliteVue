<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li>
        <a
          href="https://vuejs.org"
          target="_blank"
        >
          Core Docs
        </a>
      </li>
      <li>
        <a
          href="https://forum.vuejs.org"
          target="_blank"
        >
          Forum
        </a>
      </li>
      <li>
        <a
          href="https://chat.vuejs.org"
          target="_blank"
        >
          Community Chat
        </a>
      </li>
      <li>
        <a
          href="https://twitter.com/vuejs"
          target="_blank"
        >
          Twitter
        </a>
      </li>
      <br>
      <li>
        <a
          href="http://vuejs-templates.github.io/webpack/"
          target="_blank"
        >
          Docs for This Template
        </a>
      </li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li>
        <a
          href="http://router.vuejs.org/"
          target="_blank"
        >
          vue-router
        </a>
      </li>
      <li>
        <a
          href="http://vuex.vuejs.org/"
          target="_blank"
        >
          vuex
        </a>
      </li>
      <li>
        <a
          href="http://vue-loader.vuejs.org/"
          target="_blank"
        >
          vue-loader
        </a>
      </li>
      <li>
        <a
          href="https://github.com/vuejs/awesome-vue"
          target="_blank"
        >
          awesome-vue bwet werf
        </a>
      </li>
    </ul>

    <table>
        <tr><th>Title</th><th>Desc.</th></tr>
        <tr v-for="blog in blogs">
          <td>{{blog.Title}}</td>
          <td>{{blog.Description}}</td>
        </tr>
    </table>

  </div>



</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      blogs:[]
    }
  },
    mounted() {
      const path = require('path')
      const dbPath = path.resolve(__dirname, 'data/simple-db.sqlite')
      var sqlite3 = require('sqlite3').verbose();
      var db = new sqlite3.Database(dbPath, sqlite3.OPEN_READWRITE);

      this.blogs = [{Title:'Soevsd', Description: 'asdfvsadv'},
      {Title:'abc', Description: 'asdfvikjmnhbgfvsadv'}];
      var blogs = [];
      db.each("select id, title, description from Blog", function(err, row){
        
        blogs[row.id] = row;
      }, function(err, rowCount){
        cb(null, blogs);
      });

      console.log(blogs);
    }
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
