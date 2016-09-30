<template>
  <div class="item-view" v-show="item">
    <item :item="item"></item>
    <p class="itemtext" v-if="hasText" v-html="item.text"></p>
    <ul class="poll-options" v-if="pollOptions">
      <li v-for="option in pollOptions">
        <p>{{option.text}}</p>
        <p class="subtext">{{option.score}} points</p>
      </li>
    </ul>
  </div>
</template>

<script>
import Item from './Item.vue'

export default {

  name: 'ItemView',

  components: {
    Item
  },

  data () {
    return {
      item: {},
      pollOptions: null
    }
  },

  route: {
    data ({ to }) {
      this.$http.get('/static/item.txt')
          .then((response) => {
              console.log(JSON.parse(response.data))
              this.item = JSON.parse(response.data);
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

<style lang="stylus">

.item-view
  .item
    padding-left 0
    margin-bottom 30px
    .index
      display none
  .poll-options
    margin-left 30px
    margin-bottom 40px
    li
      margin 12px 0
    p
      margin 8px 0
    .subtext
      color #828282
      font-size 11px
  .itemtext
    color #828282
    margin-top 0
    margin-bottom 30px
  .itemtext p
    margin 10px 0
</style>
