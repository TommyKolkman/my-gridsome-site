<template>
    <BlogLayout>
        <h1>{{ $page.post.title }}</h1>
        <img :src="$page.post.featuredImage" alt="blog" />
        <div v-html="$page.post.content" class="markdown-body" />
    </BlogLayout>
</template>

<page-query>
    query Post ($path: String!) {
        post: post( path: $path ){
            title
            content
            featuredImage
        }
    }
</page-query>

<script>
    export default {
        metaInfo() {
            return {
                title: this.$page.post.title
            }
        }
    }
</script>
