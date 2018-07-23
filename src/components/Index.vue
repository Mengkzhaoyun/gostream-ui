<template>
  <v-container fluid fill-height class="grey lighten-4">
    <v-layout justify-center align-center>
      <v-flex shrink>
        <v-tooltip right>
          <v-btn
            icon
            large
            :href="source"
            target="_blank"
            slot="activator"
          >
            <v-icon large>code</v-icon>
          </v-btn>
          <span>Source</span>
        </v-tooltip>
        <v-tooltip right>
          <v-btn icon large href="https://codepen.io/johnjleider/pen/jZQNbd" target="_blank" slot="activator">
            <v-icon large>mdi-codepen</v-icon>
          </v-btn>
          <span>Codepen</span>
        </v-tooltip>
      </v-flex>
    </v-layout>
  </v-container>
</template>