<script lang="ts">
	import {
		Button,
		Checkbox,
		Form,
		FormGroup,
		RadioButton,
		RadioButtonGroup,
		Select,
		SelectItem,
		TextInput
	} from 'carbon-components-svelte';
	import { onDestroy } from 'svelte';
	export let username = '';
	export let name = '';
	export let email = '';
</script>

<Form>
	<!-- <FormGroup legendText="checkboxes">
		<Checkbox id="cb-0" labelText="Checkbox 1" />
		<Checkbox id="cb-1" labelText="Checkbox 2" />
	</FormGroup>

	<FormGroup legendText="radiogroup">
		<RadioButtonGroup name="radio-btn-grp" selected="default-selected">
			<RadioButton id="rd-btn-0" labelText="Standard" value="standard" />
			<RadioButton id="rd-btn-1" labelText="Default" value="default-selected" />
		</RadioButtonGroup>
	</FormGroup>

	<FormGroup legendText="Select">
		<Select name="test" value="one" labelText="Select">
			<SelectItem value="one" text="One" />
			<SelectItem value="two" text="Two" />
		</Select>
	</FormGroup> -->
	<FormGroup>
		<TextInput light labelText="Name" placeholder="Enter full name..." bind:value={name} />
	</FormGroup>
	<FormGroup>
		<TextInput light labelText="User name" placeholder="Enter user name..." bind:value={username} />
	</FormGroup>
	<FormGroup>
		<TextInput
			light
			labelText="Email"
			placeholder="Enter your email address..."
			bind:value={email}
		/>
	</FormGroup>
	<!-- <Button type="submit">Submit</Button> -->
</Form>
