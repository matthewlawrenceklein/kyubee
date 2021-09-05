<script>
    import DateCard from './DateCard.svelte'
    import { events } from './constants.js'
    $: calendarEvents = events 
</script>
<div class='container'>
    <div class='row'>
        {#each calendarEvents as date}
            <DateCard {date} />
        {/each}
    </div>
</div>
<style>
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->