<script>
    export let user 
    export let eventModal
</script>
<div class='main'>
    <div class='container'>
        <div class='row'>
            <h1 class=col-8>Kyubee - calendars for dumdums</h1>
            <button class='button primary' on:click={() => eventModal.set(true)}>NEW DATE</button>
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