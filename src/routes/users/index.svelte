<script context="module" lang="ts">
	export async function load({ fetch }: any) {
		const res = await fetch('https://jsonplaceholder.typicode.com/users');
		const users = await res.json();
		if (res.ok) {
			return {
				props: {
					users
				}
			};
		}

		return {
			status: res.status,
			error: new Error('Failed to fetch users.')
		};
	}
</script>

<script lang="ts">
	import {
		DataTable,
		Toolbar,
		ToolbarContent,
		ToolbarSearch,
		ToolbarMenu,
		ToolbarMenuItem,
		Button,
		Modal,
		ToastNotification
	} from 'carbon-components-svelte';
	import CreateForm from '$lib/users/create.svelte';

	export let users: any[] = [];

	let open = false;
	let name = '';
	let username = '';
	let email = '';

	let result: any;
	async function createUser() {
		let res = await fetch('https://jsonplaceholder.typicode.com/users', {
			method: 'POST',
			body: JSON.stringify({
				name,
				username,
				email
			})
		});
		result = await res.json();
		console.log('🚀 ~ file: index.svelte ~ line 52 ~ createUser ~ result', result);
	}
</script>

{#if result}
	<div class="toast">
		<ToastNotification
			kind="success"
			title="Success"
			subtitle="User created successfully"
			caption="User will not appear in the list"
			on:close={(e) => {
				e.preventDefault();
				result = null;
			}}
		/>
	</div>
{/if}

<DataTable
    sortable
	headers={[
		{ key: 'name', value: 'Name' },
		{ key: 'username', value: 'Username' },
		{ key: 'email', value: 'Email' }
	]}
	rows={users}
>
	<strong slot="title">Users</strong>
	<span slot="description" style="font-size: 1rem"> Your organization's users </span>
	<Toolbar>
		<ToolbarContent>
			<ToolbarSearch persistent    shouldFilterRows />
			<ToolbarMenu>
				<ToolbarMenuItem primaryFocus>Restart all</ToolbarMenuItem>
				<ToolbarMenuItem href="https://cloud.ibm.com/docs/loadbalancer-service">
					API documentation
				</ToolbarMenuItem>
				<ToolbarMenuItem hasDivider danger>Stop all</ToolbarMenuItem>
			</ToolbarMenu>
			<Button on:click={() => (open = true)}>+ Create new user</Button>
		</ToolbarContent>
	</Toolbar>
</DataTable>

<Modal
	bind:open
	modalHeading="Create User"
	primaryButtonText="Confirm"
	secondaryButtonText="Cancel"
	on:close={() => {
		open = false;
		name = '';
		username = '';
		email = '';
	}}
	on:click:button--secondary={() => (open = false)}
	on:submit={async () => {
		console.log(name, username, email);
		await createUser();
		if (result) {
			open = false;
			name = '';
			username = '';
			email = '';
			setTimeout(() => (result = null), 5000);
		}
	}}
>
	<CreateForm bind:name bind:username bind:email />
</Modal>

<style>
	.toast {
		position: fixed;
		top: 58px;
		right: 0;
		z-index: 1000;
	}
</style>
