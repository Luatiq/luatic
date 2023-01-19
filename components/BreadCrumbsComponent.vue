<template>
  <nav>
    <transition name="breadcrumbs">
      <ol v-if="Object.keys(breadCrumbs).length > 1" class="flex breadcrumbs">
        <li v-for="(crumb) in breadCrumbs" :key="crumb.key">
          <RouterLink :to="crumb.path">{{ crumb.display.substring(0,1).toUpperCase() + crumb.display.substring(1) }}</RouterLink>
        </li>
      </ol>
    </transition>
  </nav>
</template>

<script>
/* eslint-disable prefer-const */
export default {
  name: 'BreadCrumbsComponent',
  computed: {
    breadCrumbs () {
      let breadcrumbContent = {}
      breadcrumbContent.home = {
        display: 'home',
        path: '/',
        key: 'home'
      }

      // Filesystem routing has its issues :( route has no parent so this is extremely messy
      let prevPath = ''
      for (let i = 0; i < this.$route.matched[0].path.split('/').length; i++) {
        const RouteString = this.$route.matched[0].path.split('/')[i]

        if (RouteString) {
          breadcrumbContent[RouteString] = {
            display: RouteString,
            path: `${prevPath ? '/' + prevPath : ''}/${RouteString}`,
            key: RouteString + i
          }
        }

        prevPath = prevPath ? `${prevPath}/${RouteString}` : RouteString
      }

      return breadcrumbContent
    }
  }
}
</script>

<style scoped>
.breadcrumbs {
  list-style: none;
  padding: 0;
  margin-top: 0;
  user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  -webkit-user-select: none;
}

.breadcrumbs li {
  color: var(--linkColor);
  display: inline;
}

.breadcrumbs li:last-child {
  --linkColor: var(--textSubtle);
}

.breadcrumbs li:last-child a {
  text-decoration: none
}

.breadcrumbs li:not(:first-child):before {
  content: '/';
  margin: 0 .5em;
}

.breadcrumbs li:last-child a {
  color: var(--textSubtle);
}
</style>
