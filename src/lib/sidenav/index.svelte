<script context="module" lang="ts">
	export type Option = {
		id: string;
		label: string;
		route: string;
		icon: any;
	};
</script>

<script lang="ts">
	import { ClickableTile } from 'carbon-components-svelte';
	import { Grid, Row, Column } from 'carbon-components-svelte';
	import { page } from "$app/stores";

	export let options: Option[] = [];
	console.log($page.url.pathname)
</script>

<nav class="sidenav">
	<ul>
		{#each options as option}
			<li class:active={$page.url.pathname === option.route}>
				<ClickableTile href={option.route}>
					<span>
						<span><svelte:component this={option.icon} /></span>
						<span style="vertical-align: top;">{option.label}</span>
					</span>
				</ClickableTile>
			</li>
		{/each}
	</ul>
</nav>

<style>
	.active{
		background-color: black;
		color: white;
	}
</style>