<script>
    export let user 
    export let eventModal
</script>
<div class='main'>
    <div class='nav'>
        <div class='nav-left'>
            <button class='button primary' on:click={() => eventModal.set(true)}>NEW DATE</button>
        </div>
        <div class='nav-center'>
            <h1 class=col-8>Kyubee - calendars for dumdums</h1>
        </div>
        <div class='nav-right'>
            <button class='button error' on:click={() => user.set(null)}>LOG OUT</button>
        </div>
    </div>
</div>

<style>
    .nav{
        background-color: #141414;
    }
    h1{
        color: white;
    }

    .main{
        background-color: #404040;   
    }
</style>

<!-- markup (zero or more items) goes here -->