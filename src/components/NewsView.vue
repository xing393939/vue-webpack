<template>
    <div id="main">
        <ul class="posts">
            <li v-for="item in items">
                <p class="date" cate="tech">{{item.date}}</p>
                <a href="#!{{item.id}}">{{item.title}}</a>
          </li>
        </ul>
    </div>
    <!-- navigation -->
    <div v-show="items.length > 0">
        <a v-if="page > 1" :href="'#/news/' + (page - 1)">&lt; prev</a>
        <a v-if="page < 4" :href="'#/news/' + (page + 1)">more...</a>
    </div>
</template>

<script>

export default {

  name: 'NewsView',

  data () {
    return {
      page: 1,
      items: []
    }
  },

  route: {
    data ({ to }) {
      const page = +to.params.page
      document.title = 'Vue.js HN Clone'

      this.$http.get('/static/news.txt')
        .then((response) => {
            console.log(JSON.parse(response.data))
            this.items = JSON.parse(response.data);
            this.page = page;
        })
        .catch(function(response) {
            console.log(response)
        })
    }
  },

  created () {
  },

  destroyed () {
  },

  methods: {
    update () {
      this.$http.get('/static/news.txt')
        .then((response) => {
            console.log(JSON.parse(response.data))
            this.items = JSON.parse(response.data);
        })
        .catch(function(response) {
            console.log(response)
        })
    }
  },

  filters: {
    formatItemIndex (index) {
      return (this.page - 1) * 30 + index + 1
    }
  }
}
</script>
