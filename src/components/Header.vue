<template>
  <header class="header">

        <div class="brand">
            <div class="container">
                VUE NEWS
            </div>
        </div>

        <div class="navigation-cat">
            <div class="container">
                <ul >
                    <li :key="category" v-for="category in categories" @click="$emit('change-cat', category)">{{category}}</li>
                </ul>
            </div>


        <div class="searchbar"></div>

          
    </div>
  </header>
</template>

<script>
export default {
    name: "Header",
    data(){
        return {
            categories: [
                "Geral",
                "Esportes",
                "Tecnologia",
                "Negócios",
                "Saúde"
            ]
        }
    }
}
</script>

<style scoped>
    .header {
        width: 100%;
        box-shadow: 0px 6px 5px 0px rgba(148,148,148,1);
        background: #42b883;
    }
    .brand {
        font-size: 2em;
        color: #fff;
        padding: 5px 0;

    }
    .navigation-cat {
        background: #01796f;
        height: 40px;
    }
    .navigation-cat ul{
        display: flex;
        flex-direction: row;
        padding-top: 10px;
    }
    .navigation-cat li {
        color: #fff;
        cursor: pointer;
        list-style: none;
        padding: 0px 10px;
    }
    .navigation-cat li:hover {
        border-bottom: 2px solid #fff;
    }
</style>