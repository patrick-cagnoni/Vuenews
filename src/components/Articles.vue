<template>
    <div class="container">
        <div class="header">
            <h1>{{category}}</h1>
        </div>
        <div class="articles">
            <div class="articles-cards" :key="article.title" v-for="article in articles">
                <Article :article="article"/>
            </div>

        </div>
    </div>
</template>

<script>
import Article from "../components/Article"
export default {
    name: "Articles",
    props:["articles", "category"],
    components: {
        Article
    }
}
</script>

<style scoped>
    .articles {
        min-height: 100vh;
    }
</style>