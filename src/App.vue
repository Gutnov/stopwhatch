<template>
	<div id="app">
		<div class="stopwhatch">
			<div class="container">
				<StopwhatchList/>
			</div>
		</div>
	</div>
</template>

<script>
import StopwhatchList from '@/components/StopwhatchList'
export default {
	name: 'App',
	components: {
		StopwhatchList
	}
}
</script>

<style lang="scss">
@import '~normalize.css/normalize.css';

@font-face {
	font-family: 'Gotham Pro';
	src: url('~@/assets/fonts/GothamPro.eot');
	src: url('~@/assets/fonts/GothamPro.eot?#iefix') format('embedded-opentype'),
		url('~@/assets/fonts/GothamPro.woff2') format('woff2'),
		url('~@/assets/fonts/GothamPro.woff') format('woff'),
		url('~@/assets/fonts/GothamPro.ttf') format('truetype');
	font-weight: normal;
	font-style: normal;
	font-display: swap;
}
html{
	font-family: 'Gotham Pro', sans-serif;
	font-size: 22px;
	color: #fff;
}
button {
	background-color: transparent;
	border: none;
	padding: 0;
	margin: 0;
	line-height: 0;
	cursor: pointer;
	outline: none;
}

ul {
	padding: 0;
	margin: 0;
}
li {
	list-style: none;
}
div, a, ul, li, button, span {
	box-sizing: border-box;
}
.container {
	max-width: 870px;
	margin: 0 auto;
	padding: 0 46px;
}
.stopwhatch {
	background: #353638;
	min-height: 100vh;
	padding-top: 72px;
}

</style>