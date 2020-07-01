<template>
  <v-dialog v-model="modaldialog" @input="$root.$emit('SLIDE_SHOW_CLOSED')" >
    <v-sheet
      class="mx-auto"
      elevation="2"
    >
      <div style="position: absolute; ">
        <v-icon class="" x-large @click="closeMobileSlideShow" fixed="true" color="#D50000" >mdi-alpha-x</v-icon>
      </div>
      
      <v-row justify="center">
        <v-col v-for="n in images.length" :key="n" cols="8" md="5">
          <v-skeleton-loader
          :loading="skeletonLoading"
              transition="scale-transition"
              class="mx-auto"
              max-width="300"
              type="card">
            <div class="overline text-center font-weight-medium">-- {{ n >= 10 ? n : '0'+n }} --</div>
          <v-img
            :src="images[n-1]"
            _class="ma-2"
            _height="500" _width="300" contain/>
          </v-skeleton-loader> 
        </v-col>
        <!-- <v-btn class="mx-3" @click="closeMobileSlideShow" fixed="true" right="true" >
          <v-icon large>mdi-alpha-x</v-icon>
        </v-btn> -->
      </v-row>
    </v-sheet>
  </v-dialog>
</template>

<script>

export default {
  name: 'MobileSlideShow',



  data: () => ({
    modaldialog: true
  }),
  props: ['images'],

  methods: {
    closeMobileSlideShow () {
        this.modaldialog = false
        setTimeout(() => this.modaldialog = "true", 500)
    }

    
  }
}
</script>