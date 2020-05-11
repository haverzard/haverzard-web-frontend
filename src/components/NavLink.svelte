<script>
	import { getContext, createEventDispatcher } from "svelte";
	import { fly } from 'svelte/transition'
	import { Link,  navigate } from "svelte-routing";

	export let to = "";

	const dispatch = createEventDispatcher();

	function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
		const isActive = href === "/" ? isCurrent : isPartiallyCurrent || isCurrent;

		if (isActive) {
			return { class: "active" };
		}
		return {};
	}

	function onClick(event) {
		navigate(to, { replace: true });
	}
</script>

<style>
	.link_box {
		min-width: 150px;
		display: flex;
		justify-content: center;
		cursor: pointer;
	}
	@media (max-width: 1000px) {
		.link_box {
			width: 100%;
			height: 100px;
			display: flex;
			justify-content: center;
			font-size: 50px;
			border-top: 1px #AAA solid;
		}
	}
</style>

<div on:click="{onClick}" class="link_box" transition:fly="{{ x: -50, duration: 500 }}">
	<Link to="{to}" getProps="{getProps}">
		<slot />
	</Link>
</div>