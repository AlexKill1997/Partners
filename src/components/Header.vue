<template lang="pug">
	.header
		.header__container.container
			a.header__container__logo( href="https://qsoft.ru/")
				img(src="@/assets/Logo_qsoft.svg")
			
			.header__container__search
				img.header__container__search__icon(@click="find" src="@/assets/loupe.svg")
				input(type="text" v-model="search" placeholder="Поиск по партнерам...")
			.header__container__online(v-if="mobileVersion")
				img(src="@/assets/person.svg")
			.header__container__account( v-else)
				.header__container__account__person Константин 
				img(src="@/assets/account.png")
			
</template>
<script>
import { bus } from "@/bus.js"
export default {
	data:()=>({
		search:'',
		mobileVersion: false
	}),
	methods:{
		find(){
			console.log(window.innerWidth)
			bus.$emit('result',{search:this.search})
		},
		cons(){
			console.log(this.mobileVersion)
			this.mobileVersion = true
		}
	},
	mounted() {
    window.addEventListener('resize', () => {
        if(window.innerWidth < 481){
          this.mobileVersion = true

        }
        else this.mobileVersion = false
      })

  }
}
</script>
<style lang="sass">
.header
	width: 100%
	height: 80px
	box-shadow: 0px 3px 10px rgba(0, 0, 0, 0.05)
	display: flex
	justify-content: center
	align-items: center
	font-size: 14px
	@media screen and(max-width: 480px)
		height: fit-content
	.header__container
		height: 100%
		@media screen and(max-width: 480px)
			height: fit-content
		&__logo
			cursor: pointer
			order: 1
			height: 31px
			width: 135px
			@media screen and(max-width: 480px)
				margin: 16px 20px

			img
				width: 100%
				height: 100%
		&__search
			width: 60%
			position: relative
			order: 2
			margin: 0 10px
			@media screen and(max-width: 480px)
				order: 10
				width: 100%
				margin: 0 
			&__icon
				position: absolute
				top: 12px
				left: 12px
			input
				padding: 12px 5px 12px 39px
				width: 100%
				border: 1px solid #EBEBF1
				height: 100% 
				@media screen and(max-width: 480px)
					border: none
					border-top: 1px solid #EBEBF1
			input::placeholder
				color: #BBC4D6
		&__account
			display: flex
			border-left: 1px solid #EBEBF1
			width: 150px
			justify-content: center
			align-items: center
			padding-left: 19px
			height: 100%
			order: 3
			&__person
				font-size: 14px
				margin-right: 10px
		&__online
			order: 4
			width: 24px
			height: 24px
			margin-right: 20px
			img
				width: 100%
.header .container
	display: flex
	justify-content: space-between
	align-items: center
	@media screen and(max-width: 480px)
		flex-wrap: wrap
		padding: 0
</style>