<template>
  <div class="bolg">
    <blog-nav :content="content" :filters="filters" :navs="navs" />
    <blog-feed :filters="filters" />
    <blog-post :post="post" />
    <blog-footer/>
  </div>
</template>


<script>
  import BlogNav from './BlogNav'
  import BlogFeed from './Feeds'
  import BlogPost from './Post'
  import BlogFooter from './Footer'
  export default {
    name: 'blog',
    components: {
      BlogNav,
      BlogFeed,
      BlogPost,
      BlogFooter
    },
    resource: 'Blog',
    data () {
      return {
        navs: 0,
        title: '',
        labels: {
          post: '',
          author: ''
        }
      }
    },
    computed: {
      content () {
        return {
          title: this.title,
          labels: this.labels
        }
      },
      filters () {
        let filters = {}
        if (this.post) filters.post = this.post
        if (this.author) filters.author = this.author
        return filters
      }
    },
    watch: {
      '$route.name' (to, from) {
        if (to !== from) this.navs++
      }
    },
    beforeMount () {
      this.$getResource('blog')
    }
  }
</script>


<style scoped>

</style>
