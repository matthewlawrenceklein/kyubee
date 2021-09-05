<script>
    export let user 
    export let calendarEvents

    function handleAddDate(){
        // let newEvent =  {
        //     date : '11/11/11',
        //     title : 'KILL HITLER',
        //     details : 'at the park with mary',
        //     tags : ['MURDER', 'social']
        // }
        // calendarEvents.update([...calendarEvents, newEvent ])
        // console.log('got here')
        console.log($calendarEvents)
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