<script>
    import DateCard from './DateCard.svelte'
    import EventModal from './eventModal.svelte'
    import { writable } from 'svelte/store'
    import { onMount, beforeUpdate } from 'svelte';
    export let eventModal
    $: calendarEvents = []

    $: onMount(() =>{
        getDates()
    })

    $: beforeUpdate(() => {
        getDates()
    })

    async function getDates(){
        await fetch('http://localhost:3000/events')
                .then(resp => resp.json())
                .then(data => {
                    calendarEvents = data.events
        })
    }
</script>

<div class='main'>
    {#if $eventModal}
        <EventModal {eventModal}/>
         <!-- content here -->
    {:else}
         <button on:click={getDates}>get dates</button>
         <div class='container'>
             <div class='row'>
                 {#each [...calendarEvents] as date}
                     <DateCard {date} />
                 {/each}
             </div>
         </div>
    {/if}
</div>

<style>
    .main{
        height: 80vh;
        background: #141414;
    }

</style>

<!-- markup (zero or more items) goes here -->