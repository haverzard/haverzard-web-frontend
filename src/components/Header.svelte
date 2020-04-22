<script>
	import { Link } from "svelte-routing"
	import NavLink from "./NavLink.svelte"
	let visible = false
</script>
<style>
	#header {
		width: 100%;
		min-height: 60px;
		font-size: 5vh;
		background-color: #FFF;
		border-bottom: 1px #AAA solid;
		display: flex;
		align-items: center;
		flex-wrap: wrap;
		position: fixed;
		z-index: 1;
	}
	#list_button {
		width: 50px;
		height: 50px;
	}
	@media (max-width: 1000px) {
		#list_button {
			width: 100px;
			height: 100px;
		}
	}
</style>

<div id="header">
    <img on:click={()=> visible = !visible} id="list_button" src="images/bulletins.png" alt="=">
	{#if visible}
		<NavLink to="/">Home</NavLink>
		<NavLink to="about">About</NavLink>
		<NavLink to="projects">Projects</NavLink>
	{/if}
</div>	