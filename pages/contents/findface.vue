<template >
  <v-row justify="center"  >
    <v-col cols="12" sm="10" >
      <!-- game area row  -->
      <v-row  class="ma-2" >
        <v-col :align="align" >
          <v-card height="90%" width="100%" class="ma-2" color="#f3bad6"> 
            <v-card flat height="800px" width="100%" >
              <iframe width="100%" height="100%" src="https://findface.netlify.app" frameborder="0"></iframe>


            </v-card>
            <v-card-text> {{$t('findface.onlykorean')}}</v-card-text>

            
          </v-card>

          <h4 class="ma-2">share buttons(preparing)</h4>
          <v-btn 
          text 
          icon 
          large v-for="(share,index) in $t('depression_test.sharebutton')" 
          :key="index" 
          width="40px"  
          height="40px" 
          @click="sharing(index)"  
          color="rgba(0,0,0,0.5)" 
          class="ma-1"
          > <v-img width="40px" height="40px":src="share[1]"></v-img> 
         </v-btn>  

          

        </v-col>

      </v-row>

      <!-- idontknow area row  -->
    </v-col>
  </v-row>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  
      head() {

      return {
        
        htmlAttrs: {
          lang: this.$i18n.locale
        },

        meta: [
          { charset: 'utf-8' },
          { name: 'viewport', content: 'width=device-width, initial-scale=1' },

          { hid: 'keywords', name: 'keywords', content: this.$t('findface.meta_keywords') },
          { hid: 'description', name: 'description', content: this.$t('findface.meta_description') },
        ]
       }
      },


  components: {
    Logo,
    VuetifyLogo
  },
  data(){
    return{
      align : 'center'
    }
  },
  methods:{
    sharing(number){
      console.log(number)
  
    }
  }
}
</script>

<style>
  .theme--dark.v-application{
    color : black
  }
</style>