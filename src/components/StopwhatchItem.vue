<template>
	<li class="stopwhatch-item" :class="{runing: runing}">
		<div class="stopwhatch-item__time">
			<div>
				<span v-show="hours < 10">0</span>{{hours}}:
			</div>
			<div>
				<span v-show="minutes < 10">0</span>{{minutes}}:
			</div>
			<div>
				<span v-show="seconds < 10">0</span>{{seconds}}
			</div>
		</div>
		<div class="stopwhatch-item__buttons">
			<button v-if="runing" @click="pause">
				<svg width="3" height="20" viewBox="0 0 3 20" style="margin-right: 4px" xmlns="http://www.w3.org/2000/svg">
					<rect width="3" height="20" fill="white"/>
				</svg>
				<svg width="3" height="20" viewBox="0 0 3 20"  xmlns="http://www.w3.org/2000/svg">
					<rect width="3" height="20" fill="white"/>
				</svg>
			</button>
			<button v-else @click="run">
				<span class="stopwhatch-item__buttons-play"></span>
			</button>
			<button class="stopwhatch-item__buttons-stop" @click="stop"></button>
		</div>
	</li>
</template>

<style lang="scss">

.stopwhatch-item {
	list-style: none;
	background: #696969;
	min-width: 225px;
	max-width: 225px;
	transition: color .3s;
	&.runing {
		color: #fff;

		.stopwhatch-item__time
		{
			border-bottom-color: #fff;
			color: #fff;
		}

		.stopwhatch-item__buttons-stop{background-color: #fff;}
	}
}

.stopwhatch-item__time {
	display: flex;
	justify-content: center;
	border-bottom: 1px solid #9E9E9E;
	line-height: 60px;
	text-align: center;
	color: #9E9E9E;
	transition: all .3s;
}
.stopwhatch-item__buttons {
	display: flex;
	align-items: center;
	justify-content: space-between;
	padding: 20px 70px 20px 73px;
}
.stopwhatch-item__buttons-play {
	display: block;
	border: 0px solid transparent;
	border-bottom-width: 10px;
	border-top-width: 10px;
	border-left-width: 17px;
	border-left-color: #9E9E9E;
}
.stopwhatch-item__buttons-stop {
	background-color: #9E9E9E;
	width: 20px;
	height: 20px;
	transition: background-color .3s;
}
</style>

<script>
export default {
	name: 'StopwhatchItem',
	data() {
		return {
			runing: false,
			seconds: 0,
			minutes: 0,
			hours: 0,
			showHours: false,
			showMinutes: false,
			interval: null,
			twoDigitSeconds: true
		}
	},
	methods: {
		run() {
			this.runing = true
			this.seconds++

			this.interval = setInterval(() => {
				if(this.seconds > 8) this.twoDigitSeconds = false;
				this.seconds++
			}, 1000);
		},
		pause() {
			this.runing = false
			clearInterval(this.interval)
		},
		stop() {
			this.seconds = 0;
			this.minutes = 0;
			this.hours = 0;
			this.runing =  false;
			clearInterval(this.interval)
		},
	},
	watch: {
		seconds(val) {
			if(val > 59) {
				this.minutes+= (+Math.floor(val / 60))
				this.seconds = 0
				this.showMinutes = true
				//console.log(val)
			}
		},
		minutes(val) {
			if(val > 59) {
				this.hours+= (+Math.floor(val / 60))
				this.minutes = 0
				this.showHours = true
			}
		}
	}
	
}
</script>