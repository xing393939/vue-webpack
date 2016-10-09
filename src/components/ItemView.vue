<template>
    <h2>做一个 App 前需要考虑的几件事</h2>
    <div class="cnt">
        {{{item}}}
    </div>
</template>

<script>

export default {

  name: 'ItemView',

  data () {
    return {
      item: "loading",
      pollOptions: null
    }
  },

  route: {
    data ({ to }) {
      this.$http.get('/static/item.txt')
          .then((response) => {
              console.log(response.data)
              this.item = response.data;
          })
          .catch(function(response) {
              console.log(response)
          })
    }
  },

  computed: {
    isJob () {
      return this.item.type === 'job'
    },

    hasText () {
      return this.item.hasOwnProperty('text')
    }
  }
}
</script>
