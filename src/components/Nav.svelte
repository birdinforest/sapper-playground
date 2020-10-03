<script lang="ts">
	import Tab, {Icon, Label} from '@smui/tab/bare.js';
	import '@smui/tab/bare.css';
	import TabBar from '@smui/tab-bar/bare.js';
	import '@smui/tab-bar/bare.css';

	import {goto, prefetch} from '@sapper/app';

	// Receive tabs from `_layout.svelte`.
	export let TABS: object[] = [];

	// Current active tab.
	let activeTab: object;

	// Navigate to other page then process after navigation done.
	// https://sapper.svelte.dev/docs#goto_href_options
	const navigateAndSave = async (tab) => {
	  // Navigate to.
	  await goto(tab.url);
		// Postprocess after navigation.
		onNavigationFinished();
	}

	const onNavigationFinished = () => {
		// do something with the database
	}

	// Prefetch page
	// https://sapper.svelte.dev/docs#prefetch_href
	const prefetchPage = async (tab) => {
		// console.log('on hover', tab);
		const result = await prefetch(tab.url);
		// console.log('prefetch done: ', result);
	}

</script>

<style>
	nav {
		border-bottom: 1px solid rgba(255,62,0,0.1);
		font-weight: 300;
		padding: 0 1em;
	}
</style>

<nav>
	<TabBar tabs={TABS} let:tab bind:active={activeTab}>
		<Tab {tab} on:click={()=>navigateAndSave(tab)}  on:mouseover={()=>prefetchPage(tab)}>
			<Label>{tab.label}</Label>
		</Tab>
	</TabBar>
</nav>
