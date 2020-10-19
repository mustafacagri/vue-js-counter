<template>
	<div>
		{{value}}
	</div>
</template>

<script>
export default {
	name: "VueJsCounter",
	props:{
		start: {default:0},
		end: {default:0},
		duration: {default:2000},
		thousand: {type: String, default:"."}, // thousand seperator
		decimal: {type: String, default:","} // decimal seperator
	},
	data(){
		return{
			startData: null,
			endData: null,
			durationData: null,
			numberToSum: null,
			value: null
		}
	},
	methods:{
		numberWithCommas(value,thousand){
			return value.toString().replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, thousand);
		}
	},
	created(){
		this.startData = parseInt(this.start)
		this.endData = parseInt(this.end)
		this.durationData = parseInt(this.duration)

		if(this.startData == this.endData){
			this.value = this.startData
		}
		else{
			const frameDuration = 1000 / 60;
			const totalFrames = Math.round( this.duration / frameDuration );
			const easeOutQuad = t => t * ( 2 - t );
			let increasing = true
			if(this.startData>this.endData){this.endData == undefined ? this.endData = 0 : this.endData}
			else{
				increasing=false
				this.startData == undefined ? this.startData = 0 : this.startData
			}
			
			let frame = 0;
			const countTo = this.endData - this.startData
			if(countTo<0){countTo * -1}
			const counter = setInterval( () => {
				frame++;
				const progress = easeOutQuad( frame / totalFrames )
				const currentCount = Math.round( countTo * progress )
				if ( parseInt( this.value, 10 ) !== currentCount ) {
					this.value = this.numberWithCommas(increasing ? this.startData + currentCount : this.startData + currentCount , this.thousand)
				}
				if (frame === totalFrames) clearInterval( counter )
			}, frameDuration )
		}
	}
}
</script>