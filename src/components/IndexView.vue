<template>
  <div class="news-view">
    <!-- item list -->
    index
    <a :href="'#/item/' + 123">{{link}}</a>
    user
    <a :href="'#/user/' + 'john'">{{link}}</a>
  </div>
</template>

<script>
export default {
  data () {
    return {
      link: 'Hello World!'
    }
  }
}
</script>

<style lang="stylus">
.news-view
  padding-left 5px
  padding-right 15px
  &.loading:before
    content "Loading..."
    position absolute
    top 16px
    left 20px
  .nav
    padding 10px 10px 10px 40px
    margin-top 10px
    border-top 2px solid #f60
    a
      margin-right 10px
      &:hover
        text-decoration underline
</style>
