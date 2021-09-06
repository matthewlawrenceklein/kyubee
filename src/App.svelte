<script>
	import 'chota'
	import Dashboard from './Dashboard.svelte'
	import NavBar from './NavBar.svelte'
	import Login from './Login.svelte'
	import Footer from './Footer.svelte'
	import { writable } from 'svelte/store' 
	
	$: user = writable(null)
	$: eventModal = writable(false)
	$: calendarEvents = writable([])
</script>

{#if $user}
	<NavBar {user} {eventModal}/>
	<Dashboard {eventModal} {calendarEvents}/>
	<Footer/>
{:else}
	<Login {user} />
	<Footer/>
{/if}

<style>
</style>