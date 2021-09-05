<script>
	import NavBar from './NavBar.svelte'
	import Dashboard from './Dashboard.svelte'
	import Login from './Login.svelte'
	import Datecard from './DateCard.svelte'
	import Footer from './Footer.svelte'
	import { writable } from 'svelte/store' 
	
	$: user = writable(null)
</script>

{#if $user}
	<NavBar {user}/>
	<Dashboard/>
	<Footer/>
{:else}
	<Login {user} />
	<Footer/>
{/if}

<style>
</style>