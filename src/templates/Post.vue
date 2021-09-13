<template>
    <Layout>
        <!-- Page Header-->
        <header class="masthead"
            :style="{
                backgroundImage: `url(${URL+$page.post.cover.url})`
            }"
        >
            <div class="container position-relative px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7">
                        <div class="post-heading">
                            <h1>{{$page.post.title}}</h1>
                            <span class="meta">
                                Posted by
                                <a href="#!">Y xp</a>
                                on {{$page.post.created_at}}
                            </span>
                        </div>
                    </div>
                </div>
            </div>
        </header>
        <!-- Post Content-->
        <article class="mb-4">
            <div class="container px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7" v-html="md2Html($page.post.content)">

                    </div>
                </div>
            </div>
        </article>
    </Layout>

</template>

<page-query>
query ($id: ID!){
    post: strapiPost (id: $id){
        id
        title
        content
        cover{
            url
        }
        tags{
            id
            title
        }
    }
}
</page-query>

<script>
import MarkdownIt from 'markdown-it'
const md = new MarkdownIt()
export default {
    name: "Post",
    data() {
        return {}
    },
    created() {
    },
    methods: {
        md2Html(text){
            return md.render(text)
        }
    },
    components: {}
}
</script>

<style scoped>

</style>