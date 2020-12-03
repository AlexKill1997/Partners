<template lang="pug">
	#app
		vHeader
		vPartners  
</template>
<script>
import vHeader from '@/components/Header'
import vPartners from '@/components/Partners'
export default {
	components:{
		vHeader,
		vPartners 
	}
}
</script>
<style lang="sass">
body,html
	width: 100%
*
	box-sizing: border-box
#app
	font-family:  Roboto, sans-serif
	-webkit-font-smoothing: antialiased
	-moz-osx-font-smoothing: grayscale
body
	margin: 0
.container
	width: 1168px
	padding: 0 20px
</style>
