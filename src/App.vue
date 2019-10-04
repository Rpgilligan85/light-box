<template>
  <v-app>
    <v-content>
		<v-img @click="openLightBox()" contain src="https://storage.googleapis.com/support-kms-prod/D4EB1862C020486CCE5291B5B3E257BA4A25" />
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
    images: ["https://images.pexels.com/photos/853199/pexels-photo-853199.jpeg?"
      , "https://images.pexels.com/photos/1402787/pexels-photo-1402787.jpeg"
      ,"https://images.pexels.com/photos/1236701/pexels-photo-1236701.jpeg"
      ,"https://images.pexels.com/photos/36717/amazing-animal-beautiful-beautifull.jpg"
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

<style lang="scss">

html {
	overflow: hidden !important;
}

</style>