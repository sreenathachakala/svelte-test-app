<script>
	import {
		DataTable,
		Toolbar,
		ToolbarContent,
		ToolbarSearch,
		ToolbarMenu,
		ToolbarMenuItem,
		Button
	} from 'carbon-components-svelte';
</script>

<DataTable
	headers={[
		{ key: "name", value: "Name", width: "50%", minWidth: "200px" },
    { key: "protocol", value: "Status", width: "60px" },
    { key: "port", value: "Source", width: "60px" },
    { key: "rule", value: "Type", width: "10rem" },
	]}
	rows={[
		{
			id: 'a',
			name: 'monitoring-examples',
			protocol: 'downloading',
			port: "git",
			rule: 'local'
		},
		{
			id: 'b',
			name: 'dkube-examples',
			protocol: 'ready',
			port: "git",
			rule: 'remote'
		},
		{
			id: 'c',
			name: 'test',
			protocol: 'ready',
			port: "git",
			rule: 'local'
		},
		{
			id: 'd',
			name: 'monitoring-examples-test',
			protocol: 'error',
			port: "git",
			rule: 'local'
		}
	]}
>
	<strong slot="title">Repos</strong>
	<span slot="description" style="font-size: 1rem">
		Your organization's Repos
	</span>
	<Toolbar>
		<ToolbarContent>
			<ToolbarSearch />
			<ToolbarMenu>
				<ToolbarMenuItem primaryFocus>Restart all</ToolbarMenuItem>
				<ToolbarMenuItem href="https://cloud.ibm.com/docs/loadbalancer-service">
					API documentation
				</ToolbarMenuItem>
				<ToolbarMenuItem hasDivider danger>Stop all</ToolbarMenuItem>
			</ToolbarMenu>
			<Button>Create new Repo</Button>
		</ToolbarContent>
	</Toolbar>
</DataTable>
