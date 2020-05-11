<script>
	import { onMount } from "svelte"
	let color = ""
	let pointer = 0
    let features = [
        {
            "title": "Reliability",
            "description": "Using containerization and rust's system, Fornax offers a very secure and safe web services for both client and server"
        },
        {
            "title": "Performance",
            "description": "Built on Rust, which don't have runtime or garbage colector, and compiled into binary which is amazingly fast"
        },
        {
            "title": "Integration",
            "description": "Fornax is using python on top of rust, and it's running efficiently"
        }
    ]
</script>

<style>
	:root {
		--content-color: #ff7f50;
	}
	#contents {
		width: 100%;
		min-height: 100vh;
		display: flex;
		align-items: center;
		flex-direction: column;
	}
	.color {
		background-color: var(--content-color);
	}
	#title {
		margin-top: 100px;
		font-size: 70px;
		font-family: "Courier New", Courier, monospace;
	}
	.content_wrapper {
		width: 100%;
		margin-top: 100px;
		margin-bottom: 200px;
	} 
	#content {
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: center;
		color: #000;
		flex-wrap: wrap;
		transition: transform 500ms linear;
	}
	.content_container {
		display: flex;
		flex-direction: column;
		margin-left: 20px;
		margin-right: 20px;
	}
	.content_box {
		width: 400px;
		height: 100px;
		border-bottom: 1px #000 solid;
		font-size: 40px;
		display: flex;
		justify-content: center;
		align-items: flex-end;
	}
	.content_box2 {
		width: 400px;
		height: 200px;
		padding-top: 30px;
        font-size: 20px;
        line-height: 40px;
	}
	@media (max-width: 1000px) {
		#title {
			margin-top: 200px;
			font-size: 150px;
		}
		#content {
			background-color: var(--content-color);
		}
		.content_container {
			width: 100%;
			margin: 0;
			display: flex;
			align-items: center;
		}
		.content_container ~ .content_container::before {
			content: '';
			width: 100%;
			height: 100px;
			background-color: #333;
		}
		.content_box {
			width: 80%;
			height: 150px;
			border-bottom: 3px #fff solid;
			font-size: 80px;
		}
		.content_box2 {
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
		Fornax
	</div>
	<div class="content_wrapper">
		<div id="content" class="color">
			{#each Array(3) as _, i}
			{#if i+pointer < features.length}
			<div class="content_container">
				<div class="content_box">
					{features[i+pointer].title}
				</div>
				<div class="content_box2">
					{features[i+pointer].description}
				</div>
			</div>
			{/if}
			{/each}
		</div>
	</div>
</div>