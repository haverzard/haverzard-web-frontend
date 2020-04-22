<script>
	import { Router, Link, Route } from "svelte-routing"
	import Footer from './components/Footer.svelte'
	import Header from './components/Header.svelte'
	import Home from './routes/Home.svelte'
	import About from './routes/About.svelte'
	import Project from './routes/Project.svelte'
	export let url = ""
</script>

<style>
	.container {
		width: 100%;
		min-height: 100vh;
	}
</style>

<Router url="{url}">
	<div class="container">
		<Header/>
		<Route path="projects" component="{Project}" />	
		<Route path="about" component="{About}" />	
    	<Route path="/"><Home /></Route>
		<Footer/>
	</div>
</Router>