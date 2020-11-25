<template >
  <v-row class="fill-height">
    <v-col align="center">
      <v-card flat class="pa-6 pr-16 pl-16" width="76%" height="100%" color="rgba(0,30,0,0)">
      <div v-if="test == true">
  

            <v-slider 
            id="theme--dark.v-label"
            v-model="problems"
            color="green darken-4"
            min="0"
            max="3"
            label="Finish"
            lab
            readonly
           ></v-slider>

          <v-row class="justify-center mb-16">
            <h2> {{$t('content2.title')}} </h2>
          </v-row>
          
          <v-col class="pa-0 ma-1" v-for="(i,index) in $t('content2.'+question)"  :key="index">
            <v-checkbox :label="String(i)" v-model="list1[index]"  ></v-checkbox>
          </v-col>
          <p>{{list1}}</p>
          <v-btn class="mt-6" width="60%" height="100px" @click="sum">  다음 </v-btn>
  
        
     </div>

     <v-row v-if="test == false">
              <v-col align="center">
                <v-card flat class="pa-6" height="100%" color="rgba(50,50,0,0)" width="800px">
                  <v-row class="justify-center ">
                    <v-card-title class="display-2">{{$t('content2.result[0]')}} :</v-card-title>
                    <v-card-title class="display-2 ma-2"> {{point_sum}} {{$t('content2.result[1]')}}</v-card-title>
                    

                    <v-card-actions class="ma-2"> {{$t('content2.result[3]')}} {{point_sum}}  {{$t('content2.result[4]')}}</v-card-actions>



                  </v-row>  
                    <v-card flat width="800px" color="rgba(0,0,0,0)">
                  
                      <v-card flat class="ma-0 pa-6" width="90%"  height="20%" color="#d6e0f0" justify="center" >
                        <v-slider
                        v-model="level"
                        color="red darken-4"
                        min="0"
                        max="100"
                        label="Risk Degree"
                        readonly
                      ></v-slider>
                      <h2 class="ma-2"> {{$t('content2.yourlevel')}} {{level}} {{$t('content2.level')}}</h2>
                      <h2 class="ma-2"> "{{$t('content2.'+result_string+'.name')}}"</h2>
                      <h3 class="ma-2">{{$t('content2.'+result_string+'.explain')}}</h3>

                      <p class="ma-10">{{$t('content2.exact')}}</p>
                      </v-card>

                      <v-card flat class="ma-2 pa-6"  width="90%" height="20%" color="#d6e0f0" justify="center">
                        <h3 class="ma-2" style="color:#C62828"> ○ {{$t('content2.symptom')}} ○</h3>
                        <h4 class="ma-2"  v-for="(i,index) in $t('content2.'+result_string+'.symptom')">* {{i}} </h4>
                      </v-card>
                      <v-card flat class="ma-2 pa-6"  width="90%" height="20%" color="#d6e0f0" justify="center">
                        <h3 class="ma-2" style="color:#2E7D32">○ {{$t('content2.helpful')}} ○</h3>
                        <h4 class="ma-2" v-for="(i,index) in $t('content2.'+result_string+'.helpful')">* {{i}} </h4>
                      </v-card>

                

                      <h4 class="ma-2">share buttons</h4>
                          <v-btn 
                          text 
                          icon 
                          large v-for="(share,index) in $t('content2.sharebutton')" 
                          :key="index" 
                          width="40px"  
                          height="40px" 
                          @click="sharing(index)"  
                          color="rgba(0,0,0,0.5)" 
                          class="ma-1"
                          > <v-img width="40px" height="40px":src="share[1]"></v-img> 
                         </v-btn>  
                        
                 
                    <v-col>
                      <v-btn   class="ma-6"  color="#8d93ab" width="30%" height="65px" @click="reload">{{$t('content2.replay')}}</v-btn>
                      <v-card-text class="ma-2"> {{$t('content2.result[2]')}}</v-card-text>
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



export default {
  data(){
    return{
      question : 0,
      point_sum: 0,
      test : true,
      problems : 0,

      list1:[false,false,false,false,false,false,false,false,false,false,],

    }
  },
  methods: {

  sum(){   
    this.question = this.question +1
    this.problems = this.problems +1
    if(this.question < 4){

      this.point_sum = this.point_sum + (this.list1.join(',').match(/true/g)||[]).length

    }
    else{
      this.question = 0
      this.point_sum = 0
      this.test =! this.test

    }
  }
  },
    reload(){
    window.location.reload()
  },

  sharing(number){
    console.log(number)

  }
}
</script>


<style>

  .theme--dark.v-card{
    color: black;

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
  .v-label{
    font-size : 30px
  }

  .theme--dark.v-label{
    color : black
  }

</style>