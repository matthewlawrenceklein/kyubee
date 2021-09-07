<script>
    import DateCard from './DateCard.svelte'
    import EventModal from './eventModal.svelte'
    import { onMount } from 'svelte';
    export let calendarEvents
    export let eventModal

    onMount(() =>{
        getDates()
    })

    let getDates = () => {
        fetch('http://localhost:3000/events')
            .then(resp => resp.json())
            .then(data => {
                calendarEvents.set(data.events)
                console.log('fetched updated dates')
            })
    }
</script>

<div class='main'>
    {#if $eventModal}
        <EventModal {eventModal} {getDates}/>
    {:else}
         <div class='container'>
             <div class='row'>
                 {#if $calendarEvents}
                      {#each Object.values($calendarEvents) as dateObj}
                          <DateCard {dateObj} {getDates}/>
                      {/each}
                 {/if}
             </div>
         </div>
    {/if}
</div>

<style>
    .main{
        height: 90vh;
        background: #404040;
    }

</style>

<!-- markup (zero or more items) goes here -->