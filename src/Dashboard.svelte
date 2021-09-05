<script>
    import DateCard from './DateCard.svelte'
    import { writable } from 'svelte/store'
    import { onMount } from 'svelte';

    $: calendarEvents = []

    onMount(() =>{
        fetch('http://localhost:3000/events')
        .then(resp => resp.json())
        .then(data => {
            calendarEvents = data 
        })
    })

    function getDates(){
        fetch('http://localhost:3000/events')
        .then(resp => resp.json())
        .then(data => {
            console.log('beep', data)
        })
    }

</script>
<div class='main'>
    <button on:click={getDates}>get dates</button>
    <div class='container'>
        <div class='row'>
            {#each [...calendarEvents] as date}
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