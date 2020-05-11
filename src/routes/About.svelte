<script>
	import { onMount } from "svelte"
	let visible = true
	let color = ""
	let aboutClass = "hide"
	setTimeout(async ()=>{
		aboutClass = "show"
		setTimeout(async ()=>{
			color = "color"
			visible = false
		}, 300)
	}, 1000)
	let pointer = 0
	let abouts = []
	onMount(async function() {
		let res = await fetch("https://haverzard.com/api/db/abouts")
		abouts = (await res.json()).res
	})
</script>

<style>
	:root {
		--about-color: #007031;
	}
	#contents {
		width: 100%;
		min-height: 100vh;
		display: flex;
		align-items: center;
		flex-direction: column;
	}
	.color {
		background-color: var(--about-color);
	}
	.blink {
		animation: blink_text 0.7s infinite alternate;
	}
	@keyframes blink_text{
		0%{     color: #000;    }
		100%{    color:transparent;  }
	}
	#title {
		margin-top: 100px;
		font-size: 70px;
		font-family: "Courier New", Courier, monospace;
	}
	.about_wrapper {
		width: 100%;
		margin-top: 100px;
		margin-bottom: 200px;
	} 
	#about {
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: center;
		color: #fff;
		flex-wrap: wrap;
		transition: transform 500ms linear;
	}
	.about_back {
		position: absolute;
		min-width: 100%;
		height: 275px;
		background-color: var(--about-color);
		z-index: -1;
		transition: transform 200ms linear;
	}
	.about_container {
		display: flex;
		flex-direction: column;
		margin-left: 20px;
		margin-right: 20px;
	}
	.about_box {
		width: 250px;
		height: 75px;
		border-bottom: 1px #fff solid;
		font-size: 30px;
		display: flex;
		justify-content: center;
		align-items: flex-end;
	}
	.about_box2 {
		width: 250px;
		height: 185px;
		padding-top: 15px;
		text-align: center;
	}
	.show {
		transform: translateX(0%);
	}
	.hide {
		transform: translateX(-100%);
	}
	@media (max-width: 1000px) {
		#title {
			margin-top: 200px;
			font-size: 150px;
		}
		#about {
			background-color: var(--about-color);
		}
		.about_container {
			width: 100%;
			margin: 0;
			display: flex;
			align-items: center;
		}
		.about_container ~ .about_container::before {
			content: '';
			width: 100%;
			height: 100px;
			background-color: #eee;
		}
		.about_box {
			width: 80%;
			height: 150px;
			border-bottom: 3px #fff solid;
			font-size: 80px;
		}
		.about_box2 {
			width: 80%;
			height: 450px;
			padding-top: 50px;
			font-size: 40px;
        	line-height: 70px;
		}
	}
</style>

<div id="contents">
	<div id="title">
		About<span class="blink">_</span>
	</div>
	<div class="about_wrapper">
		{#if visible}
		<div class="about_back {aboutClass}">
		</div>
		{/if}
		<div id="about" class={color}>
			{#each Array(5) as _, i}
			{#if i+pointer < abouts.length}
			<div class="about_container">
				<div class="about_box">
					{abouts[i+pointer].name}
				</div>
				<div class="about_box2">
					{abouts[i+pointer].description}
				</div>
			</div>
			{/if}
			{/each}
		</div>
	</div>
</div>