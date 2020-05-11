<script>
	import anime from 'animejs/lib/anime.es.js'
	import { Link } from "svelte-routing"
	import NavLink from "./NavLink.svelte"
	let visible = false
	let shown = "show"
	let y
	let lastY = 99999
	function updateHeader(y) {
		let temp = lastY >= y || !y
		lastY = y ? y : lastY
		return temp ? "show" : "hide"
	}
	$: shown = updateHeader(y)
</script>
<style>
	#header {
		width: 100%;
		min-height: 60px;
		font-size: 5vh;
		background-color: #e6feff;
		display: flex;
		align-items: center;
		flex-wrap: wrap;
		position: fixed;
		z-index: 1;
		transition: transform 0.3s linear;
	}
	.show {
		transform: translateY(0%);
	}
	.hide {
		transform: translateY(-100%);
	}
	#list_button {
		width: 50px;
		height: 50px;
		cursor: pointer;
	}
	@media (max-width: 1000px) {
		#list_button {
			width: 100px;
			height: 100px;
		}
	}
</style>

<svelte:window bind:scrollY={y} />

<div id="header" class={shown}>
    <img on:click={()=> visible = !visible} id="list_button" src="images/bulletins.png" alt="=">

	{#if visible}
	<NavLink to="/">Home</NavLink>
	<NavLink to="about">About</NavLink>
	<NavLink to="projects">Projects</NavLink>
	{/if}
</div>