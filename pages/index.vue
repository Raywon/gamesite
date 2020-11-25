<template>
  <v-row justify="center">
    <v-col cols="12" sm="9">
      <!-- recommend row  -->
      <v-row class="ma-2">
        <v-col align="center">

          <v-card flat height="400px" width="400px" class="ma-2" color="rgba(1,1,1,0)">
            <v-carousel height="100%" width="500px" hide-delimiter-background cycle show-arrows-on-hover>
              <v-carousel-item v-for="(slide, index) in slides" :key="index">
                <v-img :src="colors[index]" height="100%">
                  <v-btn width="100%" height="100%" color="rgba(0,0,0,0)" :to="slide">
                    <v-row class="fill-height" justify="center">
                    </v-row>
                  </v-btn>
                </v-img>
              </v-carousel-item>
            </v-carousel>
          </v-card>

        </v-col>
      </v-row>
      <!-- list row  -->

      <v-card class="pa-6 ma-4" color="#fceef5" align="center" v-for="(page,index,indexs) in pages" :key="index">
        <h3> {{$t('content_title')[indexs][0][0]}} </h3>
        <v-row class="pa-2">
          <v-col>
            <!-- md이상의 크기일때-->
            <v-row class="d-none d-md-flex" v-for="(i,index) in 1" :key="index">
              <v-col cols="12" sm="4" v-for="(content,c_index) in page" :key="c_index">

                <v-card width="100%" height="100%" color="#f1f3f8">
                  <v-img width="100%" height="80%" :src="content.src">
                    <v-btn width="100%" height="100%" color="rgba(1,1,1,0)" class="pa-0" :to="content.to"> </v-btn>
                  </v-img>

                  <v-btn width="100%" height="20%" color="rgba(0,0,0,0)" :to="content.to">
                    <v-card flat class="ma-0 pa-0" height="100%" color="rgba(0,0,0,0)">
                      <v-list-item class="pa-0">
                        <v-list-item-content>
                          <v-list-item-title style="color: black">{{$t('content_title')[indexs][1][c_index]}}
                          </v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-card> 
                  </v-btn>
                </v-card>

              </v-col>
            </v-row>
            <!-- md미만의 크기일때-->
            <v-row class="d-sm-flex d-md-none" v-for="(i,index) in 1" :key="'i'+index" justify="center">
              <v-col cols="12" sm="6" v-for="(content,c_index) in page" :key="c_index" :cols="i === 1? 5:5">

                <v-card width="100%" height="100%" color="#f1f3f8">
                  <v-img width="100%" height="80%" :src="content.src">
                    <v-btn width="100%" height="100%" color="rgba(1,1,1,0)" class="pa-0" :to="content.to"> </v-btn>
                  </v-img>

                  <v-btn width="100%" height="20%" color="rgba(0,0,0,0)">
                    <v-card flat class="ma-0 pa-0" height="100%" color="rgba(0,0,0,0)" :to="content.to">
                      <v-list-item class="pa-0">
                        <v-list-item-content>
                          <v-list-item-subtitle style="color: black">{{$t('content_title')[indexs][1][c_index]}}
                          </v-list-item-subtitle>
                        </v-list-item-content>
                      </v-list-item>
                    </v-card>
                  </v-btn>
                </v-card>


              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-card>

    </v-col>
  </v-row>
</template>

<script>
  import Logo from '~/components/Logo.vue'
  import VuetifyLogo from '~/components/VuetifyLogo.vue'

  export default {

    computed: {
      availableLocales() {
        return this.$i18n.locales;
      }

    },

    components: {
      Logo,
      VuetifyLogo,

    },

    data() {
      return {
        align: 'center',

        colors: [
          '/panicdisorder.jpg',
          '/fineface.jpg',
          '/depression.jpg',
          '/tellmeyou.jpg',
        ],
        slides: [
          this.$i18n.locale + "/contents/Panicdisorder",
          this.$i18n.locale + "/contents/findface",
          this.$i18n.locale + "/contents/depressiontest",
          this.$i18n.locale + "/contents/tellmeyou",
        ],

        pages: {
          enjoy_pages: [

            {
              title: 'Find your nationality',
              to: '/' + this.$i18n.locale + '/contents/findface',
              src: '/fineface.jpg'
            }
          ],
          mental_pages: [

            {
              title: 'Depression Test',
              to: '/' + this.$i18n.locale + '/contents/depressiontest',
              src: '/depression.jpg'
            },
            {
              title: 'PanicDisorder',
              to: '/' + this.$i18n.locale + '/contents/Panicdisorder',
              src: '/panicdisorder.jpg'
            },
            {
              title: 'tellmeyou',
              to: '/' + this.$i18n.locale + '/contents/tellmeyou',
              src: '/tellmeyou.jpg'
            }
          ]
        },

      }
    }
  }
</script>

<style>
  .v-btn__content {
    color: black;
  }

  .theme--dark.v-card {
    color: black;
  }

  .v-card__subtitle,
  .v-card__text {
    font-size: 1.1rem;
  }
</style>