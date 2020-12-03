<template lang="pug">
	.partners
		.container
			h1.partners__heading Наши партнеры
			.partners__logos
				.partners__logos__container(v-for="item in todosByTitle") 
					img.partners__logos__container__picture(:src="require('@/assets/partners/'+item.img)")
			

</template>
<script>
import { bus } from "@/bus.js";
export default {
	data : () => ({
		search:'',
		logotypes:[
			{
				id:1,
				img:  'henkel.png',
				name: 'henkel'
			},
			{
				id:2,
				img:  'john.png',
				name: 'john deere'
			},
			{
				id:3,
				img:  'mcDon.png',
				name: 'macdonalds'
			},
			{
				id:4,
				img:  'ikea.png',
				name: 'ikea'
			},
			{
				id:5,
				img:  'reebok.png',
				name: 'reebok'
			},
			{
				id:6,
				img:  'nike.png',
				name: 'nike'
			},
			{
				id:7,
				img:  'caterpillar.png',
				name: 'caterpillar'
			}
			
		],
	}),
	created(){
			bus.$on('result', data => {
		this.search = data.search
  		})
		},

	computed:{
		todosByTitle() {
		return this.logotypes.filter(item => item.name.indexOf(this.search) !== -1)
		},
	}
 
};
</script>

<style lang="sass">
.partners
	margin: 70px 0
	display: flex
	justify-content: center
	&__heading
		text-transform: uppercase
		text-align: center
		margin: 0
		margin-bottom: 30px
		@media screen and (max-width: 768px)
			font-size: 28px
	&__logos
		display: grid
		flex-wrap: wrap
		grid-template-columns: repeat(4, minmax(150px,300px))
		grid-gap: 30px
		@media screen and(max-width: 1100px)
			grid-gap: 20px
			grid-template-columns: repeat(3, minmax(150px,350px))
		@media screen and(max-width: 650px)
			grid-template-columns: repeat(2, minmax(150px,350px))
		@media screen and(max-width: 480px)
			grid-template-columns: repeat(1, minmax(150px,500px))
		&__container
			height: 100px
			border: 1px solid #EBEBF1
			display: flex
			align-items: center
			justify-content: center
			&__picture
				@media screen and(max-width: 1100px)
					max-width: 170px

		&__container:hover
			box-shadow: -3px 0px 40px rgba(0, 0, 0, 0.1), 0px 0px 10px rgba(164, 164, 164, 0.03)
</style>