<template>
  <div id="app">
      <Header v-on:change-cat="changeCat"/>
      <Articles :articles="articles" :category="category"/>
      <Footer />

  </div>
</template>

<script>
import Header from './components/Header'
import Articles from './components/Articles'
import Footer from './components/Footer'

export default {
  name: 'app',
  components: {
    Header,
    Articles,
    Footer
  },
  data(){
    return {
      articles: [],
      category: "Geral",
    }
  },
  methods: {
    changeCat(cat) {
      let params = '';
      switch(cat){
        case 'Brasil':
          params = ''
        break
        case 'Negócios':
          params = 'category=business&'
        break
        case 'Tecnologia':
          params = 'category=technology&'
        break
        case 'Esportes':
          params = 'category=sports&'
        break
        case 'Saúde':
          params = 'category=health&'
        break
        default: params = ''
      }

      this.fetchData(params)
      
      this.category = cat;

    },
    fetchData(params){
      if(!params) params = ''
      const url = 'https://newsapi.org/v2/top-headlines?' +
          'country=br&' +
          params +
          'apiKey=APIKEY';
      const req = new Request(url);

      fetch(req)
          .then(res => res.json())
          .then(data => this.articles = data.articles) 

    }
  },
  mounted() {
    this.fetchData()
  }
}
</script>

<style>
body {
  margin: 0px;
  box-sizing: border-box;
  background: #eee;
}

ul {
  padding: 0px;
  margin: 0px;
}

.container {
  width: 1024px;
  margin: 0 auto;
}



</style>
