<script>
    import DateCard from './DateCard.svelte'
    import EventModal from './eventModal.svelte'
    import { writable } from 'svelte/store'
    import { onMount, beforeUpdate, afterUpdate } from 'svelte';
    export let calendarEvents
    export let eventModal
    // $: calendarEvents = []

    $: onMount(() =>{
        getDates()
    })

    $: beforeUpdate(() => {
        getDates()
    })

    function getDates(){
        fetch('http://localhost:3000/events')
            .then(resp => resp.json())
            .then(data => {
                calendarEvents.set(data.events) // = data.events
            })
    }
</script>

<div class='main'>
    {#if $eventModal}
        <EventModal {eventModal}/>
    {:else}
         <div class='container'>
             <button on:click={getDates}>get dates</button>
             <div class='row'>
                 {#if $calendarEvents}
                      {#each Object.values($calendarEvents) as date}
                          <DateCard {date}/>
                      {/each}
                 {/if}
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