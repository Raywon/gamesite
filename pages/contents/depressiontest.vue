<template >
  <v-row class="fill-height">
    <v-col align="center">
      <v-card flat class="pa-6" height="100%" color="rgba(0,0,0,0)">


            <!--problemspage -->
         
            <v-slider 
            id="theme--dark.v-label"depression_test
            v-if="test == true"
            v-model="problems"
            color="green darken-4"
            min="0"
            max="9"
            label="Number of surveys"
            lab
            readonly
           ></v-slider>


            <v-row class="justify-center mb-16" v-if="test == true">

              <h2> {{$t('depression_test.'+question+'.title[0]')}}</h2>
            </v-row>
  
            <v-btn v-if="test == true"
              id="button_fontsize"
              class="ma-2 mt-4 "  
              v-for="(i,index) in $t('depression_test.'+question+'.button')" 
              :color="color[index]"
              :key="index" 
              width="60%" 
              height="100px"
              @click="button($t('depression_test.'+question+'.button['+index+'][1]'))"
              > 
            <v-card-text>{{$t('depression_test.'+question+'.button['+index+'][0]')}}</v-card-text>
              
          
            </v-btn>
            <!--result page -->

            <v-row v-if="test == false">
              <v-col align="center">
                <v-card flat class="pa-6" height="100%" color="rgba(50,50,0,0)" width="800px">
                  <v-row class="justify-center ">
                    <v-card-title class="display-2">{{$t('depression_test.result[0]')}} :</v-card-title>
                    <v-card-title class="display-2 ma-2"> {{point_sum}} {{$t('depression_test.result[1]')}}</v-card-title>
                    

                    <v-card-actions class="ma-2"> {{$t('depression_test.result[3]')}} {{point_sum}}  {{$t('depression_test.result[4]')}}</v-card-actions>



                  </v-row>  
                    <v-card flat width="800px" color="rgba(0,0,0,0)">
                  
                      <v-card flat class="ma-0 pa-6" width="90%"  height="20%" color="#fceef5" justify="center" >
                        <v-slider
                        v-model="level"
                        color="red darken-4"
                        min="0"
                        max="100"
                        label="Risk Degree"
                        readonly
                      ></v-slider>
                      <h2 class="ma-2"> {{$t('depression_test.yourlevel')}} {{level}} {{$t('depression_test.level')}}</h2>
                      <h2 class="ma-2"> "{{$t('depression_test.'+result_string+'.name')}}"</h2>
                      <h3 class="ma-2">{{$t('depression_test.'+result_string+'.explain')}}</h3>

                      <p class="ma-10">{{$t('depression_test.exact')}}</p>
                      </v-card>

                      <v-card flat class="ma-2 pa-6"  width="90%" height="20%" color="#fceef5" justify="center">
                        <h3 class="ma-2" style="color:#C62828"> ○ {{$t('depression_test.symptom')}} ○</h3>
                        <h4 class="ma-2"  v-for="(i,index) in $t('depression_test.'+result_string+'.symptom')">* {{i}} </h4>
                      </v-card>
                      <v-card flat class="ma-2 pa-6"  width="90%" height="20%" color="#fceef5" justify="center">
                        <h3 class="ma-2" style="color:#2E7D32">○ {{$t('depression_test.helpful')}} ○</h3>
                        <h4 class="ma-2" v-for="(i,index) in $t('depression_test.'+result_string+'.helpful')">* {{i}} </h4>
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
                        
                 
                    <v-col>
                      <v-btn   class="ma-6"  color="#f3bad6" width="30%" height="65px" @click="reload">{{$t('depression_test.replay')}}</v-btn>
                      <v-card-text class="ma-2"> {{$t('depression_test.result[2]')}}</v-card-text>
                    </v-col>

                    </v-card> 
                </v-card>
              </v-col>
            </v-row>  


      </v-card>
    </v-col>
  </v-row>  
</template>

<script>

import result1 from '../results/result1.vue'

export default {

      head() {

      return {
        
        htmlAttrs: {
          lang: this.$i18n.locale
        },

        meta: [
          { charset: 'utf-8' },
          { name: 'viewport', content: 'width=device-width, initial-scale=1' },

          { hid: 'keywords', name: 'keywords', content: this.$t('depression_test.meta_keywords') },
          { hid: 'description', name: 'description', content: this.$t('depression_test.meta_description') },
        ]
       }
      },




  components:{
    'result1' : result1,
  },


  data(){
    return{
      color :["#33691E","#43A047","#8D6E63","#FF7043","#F44336"] ,
      question : 0,
      point_sum: 0,
      test : true,
      problems:0,
      level: 0,
      result_string:'',



    }
  },
  methods: {

    button(index) {

        this.question = this.question+1
        this.point_sum = this.point_sum + parseInt(index)
        this.problems = this.problems+1
        

        if (this.question == 10){
          this.question = 0
          this.test =! this.test

          if(this.point_sum >=0 && this.point_sum <30){
            this.level = this.point_sum
            this.result_string = this.$t('Extra_mild_depression_or_some_stress')
          }

          else if(this.point_sum >=30 && this.point_sum <60){
            this.level = this.point_sum
            this.result_string = this.$t('mild_depression')
          }
          
          else if(this.point_sum >=60 && this.point_sum <80){
            this.level = this.point_sum
            this.result_string = this.$t('moderate_depression')
          }
          
          else if(this.point_sum >=80 ){
            this.level = this.point_sum
            this.result_string = this.$t('severe_depression')
          }
          else{
            
          }

        }

  },
  testing(){
    console.log(this.point_sum)
  },

  reload(){
    this.point_sum = 0
    window.location.reload()
  },

  sharing(number){
    console.log(number)

  }

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
  .theme--dark.v-label{
    color:#C62828
  }
  #theme--dark.v-label{
    color:#2E7D32
  }

.theme--dark.v-btn{
  color:black
}

</style>