<script>
	import { Button, Menu, MenuItem, MenuSeparator, Icon } from '@perfectthings/ui';

	let menu1, menu2;
	function closeSomething(e) {
		e.preventDefault(); // prevents menu auto-closing
		menu1.close(); // manually close the menu
	}
	function onMenuClick(e) {
		const { target, button } = e.detail;
		console.log(target.dataset, button.dataset);
	}
	function action1(e) {
		e.preventDefault();
		console.log('action1');
	}
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<Button>Click me</Button>

<!-- Regular menu -->
<Menu bind:this={menu1}>
	<MenuItem data-value="add-something"><Icon name="plus" /> Add some</MenuItem>
	<MenuItem>Add some more</MenuItem>
	<MenuSeparator />
	<MenuItem on:click={closeSomething}><Icon name="close" /> Close something</MenuItem>
</Menu>

<Button data-name="button-with-menu" on:click={menu1.open}>Show menu</Button>

<!-- Context menu -->
<div class="div1">Tab</div>
<Menu type="context" targetSelector=".div1" bind:this={menu2}>
	<MenuItem shortcut="cmd+n" on:click={action1}>New window</MenuItem>
	<MenuItem shortcut="cmd+shift+n" on:click={action1}>New private window</MenuItem>
	<MenuSeparator />
	<MenuItem shortcut="cmd+shift+q" on:click={action1}>Close All Windows</MenuItem>
</Menu>
