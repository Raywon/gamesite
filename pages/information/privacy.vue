<template >
  <v-row justify="center"  >
    <v-col cols="12" sm="9" >
      <!-- game area row  -->
      <v-row  class="ma-2" >
        <v-col :align="align" >
          <v-card height="100%" width="100%" class="ma-2" color="#ffffff" flat> 
            <div v-for="(privacy_array,index) in $t('privacy_list')" :key="index">
                <v-card-title> {{privacy_array[0]}} </v-card-title>
                <v-card-actions :align="align" class="pa-4" v-for="(i,index) in privacy_array" :key="index">{{privacy_array[index+1]}}</v-card-actions>
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
      align : 'left'
    }
  }
}
</script>

<style>

  .theme--dark.v-card{
    color: black;
  }

</style>