<template >
  <v-app >
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      flat
      color="#FCCCD4"
    >
      <v-img width="50"  class="shrink ma-2 hidden-sm-and-down" src="/brain.png"> </v-img>
      <v-toolbar-title class="v-toolbar-title-color">{{$t('title')}} </v-toolbar-title>
      <v-spacer />
      
      <v-menu left origin="center center" transition="scale-transition">
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="#d6e0f0" dark v-bind="attrs" v-on="on" width="8%">
            <v-icon id="icon-color">mdi-translate</v-icon>
          </v-btn>

        </template>

        <v-list color="rgb(90,90,90,0.6)">
          <nuxt-link v-for="locale in availableLocales" :key="locale.code" :to="switchLocalePath(locale.code)">
            <v-btn class="white--text" text min-width="100%"> {{locale.name}} </v-btn>
          </nuxt-link>
        </v-list>
      </v-menu>

    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    
    <v-footer
      :absolute="!fixed"
      app
      color="#FCCCD4"
    >
      <v-card-actions> @2020 RW</v-card-actions> 
      <v-spacer></v-spacer> 
      <v-row>
        <v-col align="right">
          <v-btn text color="#111111" v-for="(i,index) in $t('information')" :key="index":to="pages[index].to"> {{ i[0] }} </v-btn>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>

export default {

  
  head() {

    return {
      
      htmlAttrs: {
        lang: this.$i18n.locale
      },
      title: this.$t('title'),
      titleTemplate: '%s - ' + this.$t('title-sub'),
      
      meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },

      { hid: 'keywords', name: 'keywords', content: this.$t('meta_keywords') },
      { hid: 'description', name: 'description', content: this.$t('meta_description') },
      ]


  }
},


  computed: {
    availableLocales() {
      return this.$i18n.locales;
    }
  },

  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
 
      right: true,



      pages :[
      {
        title:'policy',
        to:'/en/information/policy'
      },
      {
        title:'privacy',
        to:'/en/information/privacy'
      },
      {
        title:'license',
        to:'/en/information/license'
      },

      ]
     
    }
  }
}
</script>

<style>

  #v-application a{
    color :rgba(red, green, blue, 0)
  }

  .theme--dark.v-application {
    background: #ffffff;
  }

  .v-toolbar-title-color{
    color: #123123;
  }

  #icon-color{
    color: #123123;
  }

  .v-application a{
    color: #ffffff00;
  }
  .theme--dark.v-footer{
    color:black;
  }
</style>