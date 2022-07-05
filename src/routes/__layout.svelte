<script lang="ts">
	import {
		Header,
		SideNav,
		SideNavItems,
		SideNavLink,
		SkipToContent,
		Content,
		Grid,
		Row,
		Column
	} from 'carbon-components-svelte';
	import type { Option } from '$lib/sidenav/index.svelte';
	import DeployRules from 'carbon-icons-svelte/lib/DeployRules.svelte';
	import Home from 'carbon-icons-svelte/lib/Home.svelte';
	import UserMultiple from "carbon-icons-svelte/lib/UserMultiple.svelte";
	import FolderOpen from 'carbon-icons-svelte/lib/FolderOpen.svelte';

	const navOptions: Option[] = [
		{
			id: "users", 
			label: "Users", 
			route: "/users", 
			icon: UserMultiple
		},
		{
			id: 'deployments',
			label: 'Deployments',
			route: '/deployments',
			icon: DeployRules
		},
		{
			id: 'code',
			label: 'Code',
			route: '/code',
			icon: FolderOpen
		}
	];
	let isSideNavOpen = false;
</script>

<Header company="Svelte" platformName="Portal" bind:isSideNavOpen>
	<svelte:fragment slot="skip-to-content">
		<SkipToContent />
	</svelte:fragment>
</Header>

<SideNav bind:isOpen={isSideNavOpen}>
	<SideNavItems>
		{#each navOptions as option}
			<SideNavLink text={option.label} href={option.route} />
		{/each}
	</SideNavItems>
</SideNav>

<Content>
	<Grid>
		<Row>
			<Column>
				<slot />
			</Column>
		</Row>
	</Grid>
</Content>
