<template >
  <v-row justify="center"  >
    <v-col cols="12" sm="10" >
      <!-- game area row  -->

          <v-card flat height="100%" width="100%" class="ma-2"color="rgba(0,0,0,0)" align="center" >   
            
            <v-img src='/back.jpg' max-height="100%"> 

              <v-row class="mt-8" style='height: 100%;'>

                <v-col cols="12">
                  <v-row class="mt-12" :justify="justify" style='height: 100%;'>
                    <v-card outlined max-width="50%" min-width="400px" height="85%" color="rgba(150,150,150,0)">
                      <v-row :align="alignment" :justify="justify" style="height: 100%;">
                        <v-card width="100%" max-height="100%" color="rgba(255, 255, 255, 0.4)" class="pa-4 ma-5"
                          :align="alignment">

                          <v-list-item-title class="display-1 mb-1 text-wrap">  {{$t('tellmeyou.body_title1')}} </v-list-item-title>
                          <v-list-item-title class="display-1 mb-3 text-wrap"> {{$t('tellmeyou.body_title2')}} </v-list-item-title>
                          <v-list-item-subtitle class="text-wrap"> {{$t('tellmeyou.body_title3')}} </v-list-item-subtitle>




                        </v-card>

                        <v-card class="pa-4 ma-5" min-height="70%" max-height="100%" width="90%" color="rgba(255, 255, 255, 0.4)">
                          <v-row>


                            <v-col class="d-flex" cols="12" sm="12" color>
                              <v-text-field :label="$t('tellmeyou.Your_Nickname')" hide-details="auto" color="rgba(40,40,40)">
                              </v-text-field>
                            </v-col>


                            <v-col class="d-flex" cols="12" sm="4">
                              <v-select :items="$t('tellmeyou.Feeling_items')" :label="$t('tellmeyou.Feeling')" color="rgba(40,40,40)"
                                item-color="rgba(40,40,40)">
                              </v-select>
                            </v-col>

                            <v-col class="d-flex" cols="12" sm="4">
                              <v-select :items="$t('tellmeyou.Gender_items')" :label="$t('tellmeyou.Gender')" color="rgba(40,40,40)"
                                item-color="rgba(40,40,40)">
                              </v-select>
                            </v-col>

                            <v-col class="d-flex" cols="12" sm="4">
                              <v-select :items="$t('tellmeyou.Age_items')" :label="$t('tellmeyou.Age')" color="rgba(40,40,40)"
                                item-color="rgba(40,40,40)">
                              </v-select>
                            </v-col>

                            <v-col class="d-flex" cols="12" md="12">
                              <v-textarea filled name="input-7-10" :label="$t('tellmeyou.Concerns')" rows="8" color="rgba(40,40,40)">
                              </v-textarea>
                            </v-col>

                            <v-col cols="12" md="12" class="pb-5 pt-0">

                              <v-card outlined class="d-flex flex-row-reverse" color="rgba(0, 0, 0, 0)">
                                <v-btn large text color="rgba(0,0,0)" @click="overlay =! overlay">{{$t('tellmeyou.send')}}</v-btn>
                              </v-card>

                            </v-col>
                          </v-row>
                        </v-card>


                      </v-row>
                    </v-card>

                    
                  </v-row>
                </v-col>
              </v-row>
            </v-img>

            <v-card height="200px" width="90%" class="ma-2" >   
                <v-card-text> share(preparing)</v-card-text>
            </v-card>



          </v-card>

    <v-overlay :absolute="absolute" :value="overlay">

      <v-card width="300px" height="200px" class="pa-5  theme--dark.v-card" :align="alignment">
        <v-list-item-title class="headline mb-3"> {{$t('tellmeyou.send_message1')}} </v-list-item-title>
        <v-list-item-subtitle class="text-wrap mb-3"> {{$t('tellmeyou.send_message2')}} </v-list-item-subtitle>
        <v-list-item-subtitle class="text-wrap mb-7"> {{$t('tellmeyou.send_message3')}} </v-list-item-subtitle>
        <v-btn color="rgba(90,90,90,0.6)" @click="reloadPage()">
          {{$t('tellmeyou.Behappy')}}
        </v-btn>
      </v-card>
    </v-overlay>





      <!-- idontknow area row  -->
    </v-col>
  </v-row>
</template>


<script>

export default {

      head() {

      return {
        
        htmlAttrs: {
          lang: this.$i18n.locale
        },

        meta: [
          { charset: 'utf-8' },
          { name: 'viewport', content: 'width=device-width, initial-scale=1' },

          { hid: 'keywords', name: 'keywords', content: this.$t('tellmeyou.meta_keywords') },
          { hid: 'description', name: 'description', content: this.$t('tellmeyou.meta_description') },
        ]
       }
      },



  


  computed: {
    availableLocales() {
      
      return this.$i18n.locales; 
    }
  },

  data: () => ({

    justify: 'center',
    justify_panels: 'start',
    alignment: 'center',
    scrollable : true,

    fab: false,


    policy: false,
    license: false,


    direction: 'left',
    transition: 'scale-transition',

    absolute: true,
    opacity: 1,
    overlay: false,

    privacy: false,
    policy1: false,
    lisence: false,





  }),

  methods: {
    reloadPage() {
      this.overlay = true
      window.location.reload()
      console.log(navigator)
    },

    button() {
      this.privacy = !this.privacy
    },

    button1() {
      this.policy1 = !this.policy1
    },

    button2() {
      this.lisence = !this.lisence
     
    }



  }


}
</script>

<style lang="scss" scoped>
  .theme--light.v-list {
    background: rgba(90, 90, 90, 0.6);
    color: rgba(0, 0, 0);
  }

  .theme--dark.v-card {
    background-color: rgba(40, 40, 40, 0.6);
    color: #FFFFFF;
  }

  #expantion-style {
    background: rgba(90, 90, 90, 0.9);
    color: black;

  }

  #expansion-panel-header-font-size{
    font-size: 100%;

  }

  .theme--dark.v-card[data-v-2a183b29]{
    color:black
  }


  #iconcolor{ 
    color: aquamarine;
      }


</style>

