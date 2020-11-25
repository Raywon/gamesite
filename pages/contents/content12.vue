<template >
  <v-row justify="center"  >
    <v-col cols="12" sm="9" >
      <!-- game area row  -->
      <v-row  class="ma-2" >
        <v-col :align="align" >
          <v-card height="800px" width="100%" class="ma-2" >   
            <v-card-text> zz</v-card-text>
          </v-card>

            <v-card height="200px" width="100%" class="ma-2" >   
            <v-card-text> share</v-card-text>
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
      align : 'center'
    }
  }
}
</script>
