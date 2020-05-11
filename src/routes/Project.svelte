<script>
	import { onMount } from "svelte"
	let color = "color"
	let pointer = 0
	let projects = [
		{
			"name": "-",
			"description": "-",
			"link": {
				"GitHub": "-",
				"Documentation": "-"
			}
		}
	]
	onMount(async function() {
		let res = await fetch("https://haverzard.com/api/db/projects")
		projects = (await res.json()).res
		projects.forEach(p => {
			p.link = {}
			if (Date.now() < new Date(p.released_date)) {
				p.name = "???"
				p.description = `Coming soon at ${p.released_date}`
			}
		})
		res = await fetch("https://haverzard.com/api/db/project_links")
		res = (await res.json()).res
		res.forEach(val => {
			projects[val.id-1].link[val.link_name] = val.link
		})
    })
</script>
<style>
	:root {
		--projects-color-hover: #9c1757;
		--projects-color-hover-after: #ac4777;
		--projects-start-color: rgb(207,85,135,0.5);
		--projects-end-color: rgb(207,85,135,0.8);
	}
	#contents {
		width: 100%;
		min-height: 100vh;
		display: flex;
		align-items: center;
		flex-direction: column;
	}
	.blink {
		animation: blink_text 0.7s infinite alternate;
	}
	.color {
		animation: colorize 10s infinite alternate;
	}
	@keyframes colorize {
		0%{     background-color: var(--projects-start-color);    }
		100%{   background-color: var(--projects-end-color);  }
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
	.projects_wrapper {
		width: 100%;
		margin-top: 100px;
		margin-bottom: 200px;
	} 
	#projects {
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: center;
		color: #FFF;
		flex-wrap: wrap;
	}
	.projects_container {
		display: flex;
		flex-direction: column;
		justify-content: center;
		min-height: 275px;
		padding-left: 20px;
		padding-right: 20px;
		transition: background-color 1s;
	}
	.projects_container:hover {
		background-color: var(--projects-color-hover);
	}
	.projects_container:hover ~ .projects_container {
		background-color: var(--projects-color-hover-after);
	}
	.projects_container:hover .projects_box3 {
		max-height: initial;
		height: 100px;
		transform: scale(1);
	}
	.projects_box {
		width: 250px;
		height: 75px;
		border-bottom: 1px #FFF solid;
		font-size: 30px;
		display: flex;
		justify-content: center;
		align-items: flex-end;
	}
	.projects_box2 {
		width: 250px;
		height: 80px;
		padding-top: 20px;
		text-align: center;
	}
	.projects_box3 {
		width: 250px;
		height: 0;
		text-align: center;
		transform: scale(0);
		transition: all 0.3s;
	}
	@media (max-width: 1000px) {
		#title {
			margin-top: 200px;
			font-size: 150px;
		}
		.projects_container {
			width: 100%;
			display: flex;
			align-items: center;
			padding: 0;
			min-height: 650px;
		}
		.projects_container ~ .projects_container::before {
			content: '';
			width: 100%;
			height: 100px;
			background-color: #555;
		}
		.projects_container:hover .projects_box3 {
			height: 200px;
		}
		.projects_box {
			width: 80%;
			height: 150px;
			border-bottom: 3px #FFF solid;
			font-size: 80px;
		}
		.projects_box2 {
			width: 80%;
			height: 250px;
			font-size: 40px;
			padding-top: 50px;
        	line-height: 70px;
		}
		.projects_box3 {
			width: 80%;
			font-size: 40px;
			height: 200px;
			transform: scale(1);
        	line-height: 70px;
		}
	}
</style>

<div id="contents">
	<div id="title">
		Project<span class="blink">_</span>
	</div>
	<div class="projects_wrapper">
		<div id="projects" class={color}>
			{#each Array(5) as _, i}
			{#if i+pointer < projects.length}
			<div class="projects_container">
				<div class="projects_box">
					{projects[i+pointer].name}
				</div>
				<div class="projects_box2">
					{projects[i+pointer].description}
				</div>
				{#if projects[i+pointer].link}
				<div class="projects_box3">
					{#each Object.keys(projects[i+pointer].link) as key}
					<div>{key}: 
						{#if projects[i+pointer].link[key] == "-"} 
						Coming Soon
						{:else}
						<a href={projects[i+pointer].link[key]}>here</a>
						{/if}
					</div>
					{/each}
				</div>
				{/if}
			</div>
			{/if}
			{/each}
		</div>
	</div>
</div>