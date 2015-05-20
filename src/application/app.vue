<style lang="stylus">
// load core components styling
@import "src/components/core/core.styl"
// load app specific variables 
@import "src/application/variables.styl"
html, body
  font-family Verdana
  font-size 13px
  margin 0
  height 100%
  background-color $bg

ul
  list-style-type none
  padding 0
  margin 0

a
  color #000
  cursor pointer
  text-decoration none

#header
  background-color #f60
  height 24px
  position relative
  h1
    font-weight bold
    font-size 13px
    display inline-block
    vertical-align middle
    margin 0
  .source
    color #fff
    font-size 11px
    position absolute
    top 4px
    right 4px
    a
      color #fff
      &:hover
        text-decoration underline

#yc
  border 1px solid #fff
  margin 2px
  display inline-block
  vertical-align middle
  img
    vertical-align middle

.view
  transition all .4s ease
  position absolute
  &.v-enter
    opacity 0
    -webkit-transform translate3d(100px, 0, 0)
    transform translate3d(100px, 0, 0)
  &.v-leave
    opacity 0
    -webkit-transform translate3d(-100px, 0, 0)
    transform translate3d(-100px, 0, 0)
</style>

<template>
  <!-- header -->
  <div id="header">
    <a id="yc" href="http://www.ycombinator.com">
      <img src="https://news.ycombinator.com/y18.gif">
    </a>
    <h1><a href="#">Hacker News</a></h1>
    <span class="source">
      Built with <a href="http://vuejs.org" target="_blank">Vue.js</a> |
      <a href="https://github.com/yyx990803/vue-hackernews" target="_blank">Source</a>
    </span>
  </div>
  <!-- main view -->
  <div v-component="{{view}}" v-with="params:params" v-transition></div>
</template>

<script>
module.exports = {
  el: '#app',
  data: {
    view: '',
    params: {
      page: 1,
      userId: null,
      itemId: null
    }
  },
  filters: {
    fromNow: require('../filters/from-now'),
    domain: require('../filters/domain')
  },
  components: {
    'news-view': require('../views/news-view.vue'),
    'item-view': require('../views/item-view.vue'),
    'user-view': require('../views/user-view.vue')
  }
}
</script>