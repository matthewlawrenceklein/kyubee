<script>
    export let eventModal

    async function handleAddDate(){
        await fetch('http://localhost:3000/events', {
            method: 'POST', 
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({
                date: new Date, 
                title: 'blockparty'
            })
        })
    }
</script>

<button on:click={() => eventModal.set(false)}>cancel</button>

<style>
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->