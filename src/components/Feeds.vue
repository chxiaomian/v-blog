<template>
  <transition-group tag="ul" :name="transition" class="blog__feed">
    <li v-for="post in feed" class="preview" :key="post.id">
      <figure class="preview__figure" :class="figureClass" :style="getBgImg(post.image)">
        <transition name="v--fade">
          <figcaption v-if="!reading || $device.phone" class="preview__details">
            <router-link class="preview__title" :to="`/read/${post.id}`" @click.native="scrollTo(0, 220, scrollDelay)">
              {{ post.title }}
            </router-link>
            <div class="preview__meta">
              <time class="preview__published">
                  {{ prettyDate(post.published) }}
                </time>
              <router-link class="preview__author" :to="`/by/${kebabify(post.author)}`" @click.native="scrollTo(0, 220, scrollDelay)">
                {{ post.author }}
              </router-link>
            </div>
          </figcaption>
        </transition>
      </figure>
    </li>
  </transition-group>
</template>


<script>
  export default {
  }
</script>


<style scoped>

</style>
