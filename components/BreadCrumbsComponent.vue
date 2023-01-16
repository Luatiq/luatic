<template>
  <nav>
    <ol v-if="Object.keys(breadCrumbs).length > 1" class="flex breadcrumbs">
      <li v-for="(crumb) in breadCrumbs" :key="crumb.key">
        <RouterLink :to="crumb.path">{{ crumb.display[0].toUpperCase() + crumb.display.substring(1) }}</RouterLink>
      </li>
    </ol>
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

      let matchedRoutes = this.$route.matched

      for (let i = 0; i < matchedRoutes.length; i++) {
        let key = matchedRoutes[i].path.substring(1).replace(/[^a-z0-9]/, 'gi', '-')

        if (key.length) {
          breadcrumbContent[key] = {
            display: matchedRoutes[i].path.substring(matchedRoutes[i].path.lastIndexOf('/') + 1),
            path: matchedRoutes[i].path,
            key
          }
        }
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
