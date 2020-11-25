<template >
  <v-row>
    <v-col align="center">
      <v-card flat class="pa-6" height="700px" color="rgba(50,50,0,0)" width="90%">
        <v-row class="justify-center mb-16">
          <v-card-title class="display-2"> </v-card-title>
        </v-row>
        <v-btn @click="test"> 테스트버튼</v-btn>

      </v-card>
    </v-col>
  </v-row>  

</template>

<script>

export default {


  data(){
    return{
      question : 0,

    }
  },
  methods: {

  }
}
</script>


<style>

  .theme--dark.v-card{
    color: black;
    background: white;
  }
  .theme--dark.v-stepper{
    background:#f1f3f8
  }
  .theme--dark.v-stepper .v-stepper__label{
    color:black;
  }

  .theme--dark.v-stepper .v-stepper__step:not(.v-stepper__step--active):not(.v-stepper__step--complete):not(.v-stepper__step--error) .v-stepper__step__step{
    background:  rgba(255,255,255,0.5)
  }

  .theme--dark.v-stepper .v-stepper__header .v-divider{
    border-color: rgba(255,255,255,0.5)
  }

</style>