<template >
  <v-row justify="center"  >
    <v-col cols="12" sm="9" >
      <!-- game area row  -->


      <v-btn class="pa-0" width="100%" height="100%"> 

      <v-col class="ma-0 pa-0">
          <v-card  class="ma-0" color="red" width="100%" height="600px">zz</v-card>
          
          <v-card width="100%" height="200px">
            <v-list-item>
              <v-list-item-content>
  
                <v-list-item-title> zzzzzzzzzzzz</v-list-item-title>
              </v-list-item-content>
  
            </v-list-item>
          </v-card>
        </v-col>

      </v-btn>
  

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
      align : 'center'
    }
  }
}
</script>
