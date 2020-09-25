<template>
	<ul class="stopwhatch-list">
		<StopwhatchItem v-for="item in stopwhatchId" :key="item"/>
		<li class="stopwhatch-add" @click="addStopwhatch">
			<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
				<rect x="8.5" width="3" height="20" fill="#9E9E9E"/>
				<rect y="11.5" width="3" height="20" transform="rotate(-90 0 11.5)" fill="#9E9E9E"/>
			</svg>
		</li>
	</ul>
</template>

<script>
import StopwhatchItem from '@/components/StopwhatchItem'

export default {
	components: {
		StopwhatchItem
	},
	data() {
		return {
			counter: 0,
			stopwhatchId: [this.counter]
		}
	},
	methods: {
		addStopwhatch() {
			this.counter++
			this.stopwhatchId.push(this.counter)
		}
	},
}
</script>

<style lang="scss">
.stopwhatch-list {
	display: grid;
	grid-template-columns: repeat(auto-fill, minmax(225px, auto));
	grid-column-gap: 50px;
	grid-row-gap: 45px;
	justify-content: center;

}
.stopwhatch-add {
	background: #696969;
	width: 225px;
	min-height: 120px;
	display: flex;
	align-items: center;
	justify-content: center;
	cursor: pointer;
}

@media (max-width: 866px) {
	.stopwhatch-list {
	
		
	}
}	
</style>