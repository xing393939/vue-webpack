<template>
  <div class="user-view">
    user
  </div>
</template>

<script>
export default {

  name: 'UserView',

  data () {
    return {
      user: {}
    }
  }
}
</script>

<style lang="stylus">
@import "../variables.styl"

.user-view
  color $gray
  li
    margin 5px 0
  .label
    display inline-block
    min-width 60px
  .about
    margin-top 1em
  .links a
    text-decoration underline
</style>
