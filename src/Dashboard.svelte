<script>
    import DateCard from './DateCard.svelte'
    import { events } from './constants.js'
    import { writable } from 'svelte/store'

    $: calendarEvents = writable(events) 

</script>
<div class='main'>
    <div class='container'>
        <div class='row'>
            {#each $calendarEvents as date}
                <DateCard {date} />
            {/each}
        </div>
    </div>
</div>

<style>
    .main{
        height: 80vh;
        background: #141414;
    }

</style>

<!-- markup (zero or more items) goes here -->