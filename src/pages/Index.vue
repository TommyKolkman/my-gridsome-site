<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <g-image alt="Example image" src="~/favicon.png" width="135" />

    <h1>Hello, world!</h1>

    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur excepturi labore tempore expedita, et iste tenetur suscipit explicabo! Dolores, aperiam non officia eos quod asperiores
    </p>

    <h2>Manual</h2>

    <ul>
      <li><g-link to="/blog-html/blog-post-one">Blogpost one</g-link></li>
      <li><g-link to="/blog-html/blog-post-two">Blogpost two</g-link></li>
      <li><g-link to="/blog-html/blog-post-three">Blogpost three</g-link></li>
    </ul>

    <h2>Markdown</h2>

    <ul>
      <li v-for="post in $page.posts.edges" :key="post.id">
        <g-link :to="post.node.path">
          {{ post.node.title }}
        </g-link>
      </li>
    </ul>

    <h2>Reddit</h2>

    <ul>
      <li v-for="redditPost in $page.redditPosts.edges" :key="redditPost.id">
        <g-link :to="redditPost.node.path">
          {{ redditPost.node.title }}
        </g-link>
      </li>
    </ul>

    <p class="home-links">
      <a href="https://gridsome.org/docs/" target="_blank" rel="noopener">Gridsome Docs</a>
      <a href="https://github.com/gridsome/gridsome" target="_blank" rel="noopener">GitHub</a>
    </p>

  </Layout>
</template>

<page-query>
  query Posts {
    posts: allPost (sortBy: "title", order: ASC) {
      edges {
        node {
          path
          title
          id
        }
      }
    }
    redditPosts: allRedditPost {
      edges {
        node {
          id
          title
          path
          thumbnail
          img
        }
      }
    }
  }
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
