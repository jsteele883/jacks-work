<template>
  <header class="navbar">
    <SidebarButton @toggle-sidebar="$emit('toggle-sidebar')"/>

    <router-link
      :to="$localePath"
      class="home-link"
    >
      <img
        class="logo"
        v-if="$site.themeConfig.logo"
        :src="$withBase($site.themeConfig.logo)"
        :alt="$siteTitle"
      >
      <div class="logo">
        <h1 class="site-name" v-if="$siteTitle">
          <span v-for="letter in $siteTitle">{{ letter }}</span>
        </h1>
      </div>
    </router-link>

    <div
      class="links"
      :style="{
        'max-width': linksWrapMaxWidth + 'px'
      }"
    >
      <AlgoliaSearchBox
        v-if="isAlgoliaSearch"
        :options="algolia"
      />
      <SearchBox v-else-if="$site.themeConfig.search !== false"/>
    </div>
  </header>
</template>

<script>
import SidebarButton from './SidebarButton.vue'
import AlgoliaSearchBox from './AlgoliaSearchBox.vue'
import SearchBox from './SearchBox.vue'
import NavLinks from './NavLinks.vue'

export default {
  components: { SidebarButton, NavLinks, SearchBox, AlgoliaSearchBox },

  data () {
    return {
      linksWrapMaxWidth: null
    }
  },

  mounted () {
    const MOBILE_DESKTOP_BREAKPOINT = 719 // refer to config.styl
    const NAVBAR_VERTICAL_PADDING = parseInt(css(this.$el, 'paddingLeft')) + parseInt(css(this.$el, 'paddingRight'))
    const handleLinksWrapWidth = () => {
      if (document.documentElement.clientWidth < MOBILE_DESKTOP_BREAKPOINT) {
        this.linksWrapMaxWidth = null
      } else {
        this.linksWrapMaxWidth = this.$el.offsetWidth - NAVBAR_VERTICAL_PADDING -
          (this.$refs.siteName && this.$refs.siteName.offsetWidth || 0)
      }
    }
    handleLinksWrapWidth()
    window.addEventListener('resize', handleLinksWrapWidth, false)
  },

  computed: {
    algolia () {
      return this.$themeLocaleConfig.algolia || this.$site.themeConfig.algolia || {}
    },

    isAlgoliaSearch () {
      return this.algolia && this.algolia.apiKey && this.algolia.indexName
    }
  }
}

function css (el, property) {
  // NOTE: Known bug, will return 'auto' if style value is 'auto'
  const win = el.ownerDocument.defaultView
  // null means not to return pseudo styles
  return win.getComputedStyle(el, null)[property]
}
</script>

<style lang="stylus">
@import '../styles/config.styl'

$navbar-vertical-padding = 0.7rem
$navbar-horizontal-padding = 1.5rem

.navbar
  padding $navbar-vertical-padding $navbar-horizontal-padding
  line-height $navbarHeight - 1.4rem
  position relative
  .links
    padding-left 1.5rem
    box-sizing border-box
    background-color white
    white-space nowrap
    font-size 0.9rem
    position absolute
    right $navbar-horizontal-padding
    top $navbar-vertical-padding
    display flex
    .search-box
      flex: 0 0 auto
      vertical-align top
    .nav-links
      flex 1

@media (max-width: $MQMobile)
  .navbar
    padding-left 4rem
    .can-hide
      display none
    .links
      padding-left 1.5rem
</style>
<style lang="scss">
  $brand1: #084C61;
  $light: hsla(75%, 90%, 92%, 1);
  $grey: #121619;
  $brand2: hsla(37%, 100%, 88%, 1);
  $logo: #E58F65;

  @import url('https://fonts.googleapis.com/css?family=DM+Serif+Text|Karla:400,700&display=swap');
  @import url('https://fonts.googleapis.com/css?family=Nunito+Sans:300,600&display=swap');
  @import url('https://fonts.googleapis.com/css?family=Roboto+Condensed:400,700&display=swap');

  .logo {
    grid-area: logo;
    width: 100px;
    height: 100px;
    .site-name {
      display: grid;
      grid-template-columns: repeat(4,1fr);
      grid-template-rows: repeat(4,1fr);
      color: $brand1;
      border-radius: 100%;
      border: 5px solid $brand1;
      background: $light;
      width: 100%;
      height:100%;
      text-align:center;
      transform: rotate(-45deg);
      font-size: 16px;
      span:nth-child(1) {
        grid-column: 2;
        grid-row: 1;
      }
      span:nth-child(2) {
        grid-column: 3;
        grid-row: 1;
      }
      span:nth-child(3) {
        grid-column: 3;
        grid-row: 2;
      }
      span:nth-child(4) {
        grid-column: 4;
        grid-row: 2;
      }
      span:nth-child(5) {
        grid-column: 1;
        grid-row: 3;
      }
      span:nth-child(6) {
        grid-column: 2;
        grid-row: 3;
      }
      span:nth-child(7) {
        grid-column: 3;
        grid-row: 3;
      }
      span:nth-child(8) {
        grid-column: 4;
        grid-row: 3;
      }
      span:nth-child(9) {
        grid-column: 2;
        grid-row: 4;
      }
      span:nth-child(10) {
        grid-column: 3;
        grid-row: 4;
      }
    }
  }
</style>
