<template>
  <v-app>
    <v-content>
		<v-btn @click="openLightBox()">Click Me</v-btn>
      <LightBox v-if="showLightBox" :images="images"/>
    </v-content>
  </v-app>
</template>

<script>
import LightBox from './components/LightBox';
import { mapActions, mapState } from 'vuex'

export default {
  name: 'App',
  components: {
    LightBox,
  },
  data: () => ({
    images: [
      {
        src: "https://images.unsplash.com/photo-1555685812-4b943f1cb0eb?ixlib=rb-1.2.1&w=1000&q=80"
      },
      {
        src: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg"
      },
      {
        src: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg"
      },
      {
        src: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg"
      }
	],
	clicked: false
  }),
  	computed: {
		...mapActions(['updateLightBox']),
		...mapState(['showLightBox']),
	},
	methods: {
		openLightBox() {
			this.$store.dispatch('updateLightBox', true)
		}
  }
};
</script>
