<template>
  <div class="post-info">
    <div class="blog-tags">
      <router-link
        v-for="tag in $frontmatter.tags"
        :to="'/tag/' + tag"
        class="blog-tag md"
      >#{{ tag }}</router-link>
    </div>
    <FeaturedPosts />
    <h3>Follow Me!</h3>
    <div>
      If you read this far, you might want to follow me on
      <a href="https://twitter.com/pydanny">
        Twitter
        <i>
          <TwitterIcon />
        </i>
      </a> or
      <a href="https://github.com/pydanny">
        Github
        <i>
          <GithubIcon />
        </i>
      </a>
    </div>
  </div>
</template>

<script>
import { GithubIcon, TwitterIcon } from "vue-feather-icons";
import FeaturedPosts from "../components/FeaturedPosts.vue";

export default {
  components: { GithubIcon, TwitterIcon, FeaturedPosts }
};
</script>

<style lang="stylus" scoped></style>

<style lang="stylus">
.post-info {
  margin-top: 3rem;
  margin-bottom: 3rem;
}
</style>

