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
    { key: "port", value: "Deployment", width: "60px" },
    { key: "rule", value: "Monitor status", width: "10rem" },
	]}
	rows={[
		{
			id: 'a',
			name: 'insurance-mm-kf',
			protocol: 'active',
			port: "production",
			rule: 'active'
		},
		{
			id: 'b',
			name: 'image-mm-kf',
			protocol: 'active',
			port: "test",
			rule: 'active'
		},
		{
			id: 'c',
			name: 'insurance-mm-kf-2',
			protocol: 'starting',
			port: "production",
			rule: 'NA'
		},
		{
			id: 'd',
			name: 'image-mm-kf-2',
			protocol: 'error',
			port: "test",
			rule: 'NA'
		},
		{
			id: 'e',
			name: 'insurance-mm-kf-3',
			protocol: 'active',
			port: "production",
			rule: 'active'
		},
		{
			id: 'f',
			name: 'image-mm-kf-3',
			protocol: 'active',
			port: "test",
			rule: 'active'
		},
	]}
>
	<strong slot="title">Deployments</strong>
	<span slot="description" style="font-size: 1rem">
		Your organization's deployments
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
			<Button>Create Deployment</Button>
		</ToolbarContent>
	</Toolbar>
</DataTable>
