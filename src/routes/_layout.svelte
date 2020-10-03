<script lang="ts">
	import Nav from '../components/Nav.svelte';

	export const TABS = [
		{ id: 'tab-home', icon: 'fas fa-plus', label: 'Home', url: '.'},
		{ id: 'tab-component', icon: 'fas fa-plus', label: 'Component', url: 'components'},
		{ id: 'tab-svelte-gl', icon: 'fas fa-arrows-alt', label: 'Svelte-gl', url: 'svelte-gl' },
		{ id: 'tab-about', icon: 'fas fa-arrows-alt', label: 'About', url: 'about' },
		{ id: 'tab-blog', icon: 'fas fa-arrows-alt', label: 'Blog', url: 'blog' },
	];

	export let segment = 'index';
</script>

<style>
	main {
		position: relative;
		max-width: 56em;
		background-color: white;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}
</style>

<Nav {TABS}/>

<main>
	<slot></slot>
</main>
