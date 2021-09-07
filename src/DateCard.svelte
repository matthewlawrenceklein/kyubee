<script>
    export let dateObj;
    export let getDates
    let showEditPage = false
    $: details = null
    $: title = null
    $: date = null
    $: tags = null

    const handleUpdateEvent = (e) => {
        e.preventDefault()
        putEvent()
        getDates()
        handleFlipCard()
    }

    const handleFlipCard = () => {
        console.log(`set card flip status to ${showEditPage}`)
        showEditPage = !showEditPage
    }

    async function putEvent(){
        await fetch(`http://localhost:3000/events/${dateObj.id}`, {
            method: 'PUT', 
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({
                id : dateObj.id, 
                date: date ? date : dateObj.date,
                title: title ? title : dateObj.title,
                details: details ? details : dateObj.details
            })
        })
        .then((resp) => {
           console.log(resp) 
        })
        .catch(err => {
            console.log(err)
        })
    }

</script>

<div class='container card'>
    {#if !showEditPage}
        <div on:click={handleFlipCard} class='card-details-container'>
            <header class='heading'>
                <h3>{dateObj.date}</h3>
            </header>
            <ul>
                <li>{dateObj.title}</li>
                <li>{dateObj.details}</li>
                {#if dateObj.tags}
                    {#each dateObj.tags as tag}
                    <li><strong>{tag}</strong></li>
                    {/each}
                {/if}
            </ul>
        </div>
    {:else}
        <form>
            <input type='date' placeholder={dateObj.date} bind:value={date}/>
            <input type='text' placeholder={dateObj.title} bind:value={title}/>
            <input type='text' placeholder={dateObj.details} bind:value={details}/>
            <div class='row'>
                <button type='submit' class='button primary' on:click={handleUpdateEvent}>Edit Event</button>
                <button class='button error' on:click={handleFlipCard}>Cancel</button>
            </div>
        </form>
    {/if}
</div>

<style>
    .card {
        width: 280px;
        height: 200px;
        margin: 10px;
        margin-top: 20px;
    }

    .card-details-container{
        min-height: 199px;
        min-width: 279px;
    }
</style>

<!-- markup (zero or more items) goes here -->