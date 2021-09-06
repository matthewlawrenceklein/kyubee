<script>
    export let user 
    export let calendarEvents

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
<div class='main'>
    <div class='container'>
        <div class='row'>
            <h1 class=col-8>Kyubee - calendars for dumdums</h1>
            <button class='button primary' on:click={() => handleAddDate()}>NEW DATE</button>
            <button class='button error' on:click={() => user.set(null)}>LOG OUT</button>
        </div>
    </div>
</div>

<style>
    .container{
        width: 100vw;
        height: 150px;
        background-color: darkslategrey;
        justify-content: center;
        align-items: center;
        vertical-align: middle;
    }
    h1{
        color: white;
    }

    .main{
        background: #141414;   
    }
</style>

<!-- markup (zero or more items) goes here -->