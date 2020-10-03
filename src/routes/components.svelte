<svelte:head>
  <title>components</title>
</svelte:head>

<h3>Min width tabs</h3>

<script lang="ts">
  import Tab, {Icon, Label} from '@smui/tab/bare.js';
  import '@smui/tab/bare.css';
  import TabBar from '@smui/tab-bar/bare.js';
  import '@smui/tab-bar/bare.css';

  export const TABS = [
    { id: 'tab-component', icon: 'fas fa-plus', label: 'Component' },
    { id: 'tab-svelte-gl', icon: 'fas fa-arrows-alt', label: 'Svelte-gl' },
  ];

  let activeTab;

  function clicked(tab) {
    alert('You clicked: ' + tab.label + ' (' + tab.id + ')');
  }
</script>

<TabBar tabs={TABS} let:tab bind:active={activeTab}>
  <Tab {tab} minWidth on:click={()=>clicked(tab)}>
    <Icon class={tab.icon} />
    <Label>{tab.label}</Label>
  </Tab>
</TabBar>

