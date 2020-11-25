<template >
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" >

      <v-card >
        <v-card-title class="headline">
          welcome to my gamesite. 
        </v-card-title>
        <v-card-text>
         
          <p>
            For more information on Vuetify, check out the <a
              href="https://vuetifyjs.com"
              target="_blank"
              rel="noopener noreferrer"
            >
              documentation
            </a>.
          </p>

        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            to="/en/inspire"
          >
            Continue
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>

export default {
  components: {

  }
}
</script>
