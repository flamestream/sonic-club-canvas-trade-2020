<template>
  <v-container class="pa-0">
    <v-card flat tile class="d-flex">
      <v-row
        class="fill-height ma-0"
        align="center"
        justify="center"
      >
        <v-img
          :src="previewPath && `entries/${previewPath}`"
          aspect-ratio="1"
          :contain="true"
          background-color="grey darken-4"
          class="img"
        >
          <v-row align="end" class="description white--text fill-height ma-0">
            <v-col align="end">
              <v-btn v-if="downloadPath" class="mr-2" fab x-small dark :href="downloadPath">
                <v-icon>mdi-download</v-icon>
              </v-btn>
              <v-avatar color="blue-grey darken-4">
                <img v-if="avatarUrl"
                  :src="avatarUrl"
                >
                <span v-else class="white--text headline">?</span>
              </v-avatar>
            </v-col>
          </v-row>
          <template v-slot:placeholder>
            <v-row class="fill-height" align="center">
              <v-col align="center" class="font-weight-black">
                NOW<br/>PRINTING
              </v-col>
            </v-row>
          </template>
        </v-img>
      </v-row>
    </v-card>
  </v-container>
</template>

<script>
  export default {
    name: 'Entry',
    props: ['previewPath', 'downloadPath', 'avatarUrl']
  }
</script>

<style scoped>
  .description {
    /*box-shadow: 0 0 20px inset rgba(0, 0, 0, 0.2);*/
    /*background: rgba(0, 0, 0, 0.8);*/
  }
  .img {
    background: #212121;
  }
</style>
