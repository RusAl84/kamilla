<template>
  <q-page class="flex flex-center">
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-vertical.svg"
      style="width: 200px; height: 200px"
    >
    <q-input rounded standout v-model="text" label="Rounded standout" />
    <q-btn round color="purple" glossy icon="local_grocery_store"  @click="this.btnClick"/>
    {{text}}
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';
import { ref } from 'vue'
import axios from "axios";
export default {
  setup () {
    return {
      text: ref('Sadikov')
    }
  },
  methods: {
  btnClick(){
    axios.post('http://127.0.0.1:5000/api/test', {
      "name":this.text,
    })
      .then(function (response) {
        console.log(response);
        alert(response.data['name'])
      })
      .catch(function (error) {
        console.log(error);
      });

    // alert(data.name)
  }
  }
}
</script>
