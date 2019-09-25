<template>
<div @click.self="closeLightBox()" class="overlay">
	<v-row @click.self="closeLightBox()" xs justify="center" align="center">
	<v-card class="container">
		<v-icon @click="closeLightBox()" class="close-btn" size="36px">mdi-close</v-icon>
		<v-carousel height="auto" max-height="95%">
			<v-carousel-item
			v-for="(item,i) in images"
			:key="i"
			:src="item.src"
			reverse-transition="fade-transition"
			transition="fade-transition"
			></v-carousel-item>
		</v-carousel>
	</v-card>
	</v-col>
	</v-row>
</div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
	props: ['images'],
	data: () => ({
		
	}),
	computed: {
		...mapActions(['updateLightBox']),
	},
	methods:{
		closeLightBox() {
			this.$store.dispatch('updateLightBox',false)
		}
	}, 

};
</script>
<style lang="scss">
	.overlay {
		display: flex;
		height: 100vh;
		width: 100vw;
		background: rgba(0,0,0,0.8);
		position: absolute;
		top:0;
		left:0;
	}

	.close-btn {
		position: absolute !important;
		right: 0px;
		top: -40px;
		z-index: 100;
		color: #666 !important;
		cursor: pointer;
	}

	.close-btn:hover {
		color: #fff !important;
	}
</style>