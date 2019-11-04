<template>
    <a :href="article.url" target="_blank">
    <div class="articlecard">
            <div class="article-img">
                <img :src="article.urlToImage">

            </div>
            <div class="article-content">
                    <h3 class="article-title">{{article.title}}</h3>
                    <p class="article-desc">{{article.description}}</p>
                    <div class="metadata"> {{format(Date.parse(article.publishedAt), "dd 'de' MMMM 'de' yyyy'", {locale})}}</div>
            </div>
    </div>
    </a>
</template>

<script>
import {format} from 'date-fns';
import locale from 'date-fns/locale/pt-BR'
export default {
    name: "Article",
    props:["article"],
    methods: {
        getDate(publishedAt){
            let date = publishedAt.substr(0, 10);
            date = date.split('-');
            return ` ${date[2]}-${date[1]}-${date[0]}`
        },
        format
    },
    data(){
        return {
            locale
        }
    }
}
</script>

<style scoped>
    a {
        text-decoration: none;
    }
    .articlecard{
        padding: 10px;
        background-color: #fff;
        color: #333;
        display: flex;
        flex-direction: row;
        flex: 0 1 50%;
        width: 80%;
        margin: 0 auto;
        margin-bottom: 20px;
    }

    .article-content {
        margin-left: 10px;
        display: flex;
        flex-direction: column;
        align-content:space-between; 
        height: inherit;
    }

    .article-img img{
        width: 232px;
        height: 130.5px;
    }

    .article-title {
        margin: 0px;
        font-weight: bold;
        font-size: 1.4em;
    }

    .article-desc {
        min-height: 40px;
    }
    .metadata {
        font-size: 0.9em;
    }

</style>