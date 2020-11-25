<template >
  <v-row justify="center"  >
    <v-col cols="12" sm="9" >
      <!-- game area row  -->
      <v-row  class="ma-2" >
        <v-col :align="align" >
          <v-card height="100%" width="100%" class="ma-2" color="#ffffff" flat :align="alignleft"> 
            

            <div class="py-3 ma-6">
              <div  :align="align">
                
                <v-btn text href="https://opensource.org/licenses/MIT" target="_blank" large color="#111111"> MIT License</v-btn>
      
              </div>
    
              <v-list-item-subtitle class="text-wrap pa-2">Copyright © 2020 Tellmeyou Developer
              </v-list-item-subtitle>
    
              <v-list-item-subtitle class="text-wrap pa-2">Permission is hereby granted, free of charge, to any person
                obtaining a copy of this software and associated documentation files (the "Software"), to deal in the
                Software without restriction, including without limitation the rights to use, copy, modify, merge, publish,
                distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is
                furnished to do so, subject to the following conditions:</v-list-item-subtitle>
    
              <v-list-item-subtitle class="text-wrap pa-2">The above copyright notice and this permission notice shall be
                included in all copies or substantial portions of the Software.</v-list-item-subtitle>
    
              <v-list-item-subtitle class="text-wrap pa-2">THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
                EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
                PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM,
                DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
                CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.</v-list-item-subtitle>
    
              <v-list-item-subtitle class="text-wrap pa-2 pb-6">This website is created using</v-list-item-subtitle>
              <v-card flat color="#ffffff" :align="align">
                  
                  <v-btn color="#111111" text href="https://vuetifyjs.com/en/" target="_blank"> Vuetify </v-btn>
                  <v-btn color="#111111" text href="https://materialdesignicons.com/" target="_blank"> Mdi icon </v-btn>
                  <v-btn color="#111111" text href="https://pixabay.com/" target="_blank"> pixabay </v-btn>

                  
        
              </v-card>
    
    
            </div>


          </v-card>
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
  components: {
    Logo,
    VuetifyLogo
  },
  data(){
    return{
      align : 'center',
      alignleft : 'left',
    }
  }
}
</script>

<style>

  .theme--dark.v-card{
    color: black;
  }

</style>