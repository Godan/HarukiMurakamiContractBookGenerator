<template>
  <v-container grid-list-md >
        <v-layout wrap>
        <v-flex  xs6 height=80vh>
          <v-textarea
            outlined
            label="変換前"
            v-model="text"
            class="page"
            rows="34"
          >
          </v-textarea>
        </v-flex>
        <v-flex  xs6>
          <v-textarea
            outlined
            name="input-7-4"
            label="変換後"
            :value="convart(text)"
            rows="34"
          ></v-textarea>
        </v-flex>
      </v-layout>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'
import axios from 'axios'

@Component
export default class PostPreview extends Vue {
  text: string = ''

  convart(text) {
   var out = text.replace(/甲/g, '僕');
   out = out.replace(/乙/g, '君');

   return out
  }

  mounted () {
    axios
      .get('./text.md')
      .then(response => (this.text = response.data))
  }
}

</script>
