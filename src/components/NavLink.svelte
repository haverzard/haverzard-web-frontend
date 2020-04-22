<script>
	import { fly } from 'svelte/transition'
	import { Link } from "svelte-routing";

	export let to = "";

	function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
	const isActive = href === "/" ? isCurrent : isPartiallyCurrent || isCurrent;

	// The object returned here is spread on the anchor element's attributes
	if (isActive) {
		return { class: "active" };
	}
		return {};
	}
</script>

<style>
	.link_box {
		min-width: 150px;
		display: flex;
		justify-content: center;
	}
	@media (max-width: 1000px) {
		.link_box {
			width: 100%;
			display: flex;
			justify-content: center;
			font-size: 50px;
			border-top: 1px #AAA solid;
		}
	}
</style>

<div class="link_box" transition:fly="{{ x: -50, duration: 500 }}">
	<Link to="{to}" getProps="{getProps}">
		<slot />
	</Link>
</div>