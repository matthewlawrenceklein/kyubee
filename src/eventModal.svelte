<script>
    import { onMount } from "svelte";
    export let eventModal
    export let getDates
    $: date = null 
    $: title = null 
    $: details = null 

    async function handleAddDate(e){
        e.preventDefault()
        console.log('got here')
        await fetch('http://localhost:3000/events', {
            method: 'POST', 
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({
                date: date,
                title: title,
                details: details
            })
        })
        .then(() => {
            getDates()
            eventModal.set(false)
        })
        .catch(err => {
            console.log(err)
        })
    }
</script>
<div class='container'>
    <button class='button error' on:click={() => eventModal.set(false)}>cancel</button>
    <form>
        <input type='date' bind:value={date}/>
        <input type='text' bind:value={title} placeholder='title'/>
        <input type='text' bind:value={details} placeholder='details'/>
        <button type='submit' on:click={handleAddDate} class='button primary'>Submit</button>
    </form>
</div>

<style>
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->