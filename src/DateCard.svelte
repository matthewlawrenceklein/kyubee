<script>
    import '@cds/core/icon/register.js';
    import { ClarityIcons, trashIcon, stopIcon, checkIcon } from '@cds/core/icon';
    ClarityIcons.addIcons(trashIcon, stopIcon, checkIcon);

    export let dateObj;
    export let getDates
    let showEditPage = false
    $: details = null
    $: title = null
    $: date = null
    $: tags = null

    const handleUpdateEvent = async(e) => {
        e.preventDefault()
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
        .then(resp => console.log(resp))
        .catch(err => console.log(error))
        getDates()
        handleFlipCard()
    }

    const handleDestroyEvent = async(e) => {
        e.preventDefault()

        await fetch(`http://localhost:3000/events/${dateObj.id}`, {
            method: 'DELETE', 
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({
                id : dateObj.id, 
            })
        })
        .then(resp => console.log(resp))
        .catch(err => console.log(error))
        getDates()
        handleFlipCard()
    }

    
    async function putEvent(){
        
    }
    
    const handleFlipCard = () => {
        console.log(`set card flip status to ${showEditPage}`)
        showEditPage = !showEditPage
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
                <button type='submit' class='button primary col-3' on:click={handleUpdateEvent}><cds-icon shape="check" size='xl'></cds-icon></button>
                <button class='button error col-3' on:click={handleFlipCard}><cds-icon shape="cancel" size='xl'></cds-icon></button>
                <button class='button error col-3' on:click={handleDestroyEvent}> <cds-icon shape="trash" size='xl'></cds-icon></button>
            </div>
        </form>
    {/if}
</div>

<style>
    .card {
        width: 380px;
        height: 300px;
        margin: 10px;
        margin-top: 20px;
    }

    .card-details-container{
        min-height: 299px;
        min-width: 379px;
    }
</style>

<!-- markup (zero or more items) goes here -->