<script>
    export let user 
</script>
<div class='container'>
    <div class='row'>
        <h1 class=col-10>Kyubee - calendars for dumdums</h1>
        <button class='button error' on:click={() => user.set(null)}>LOG OUT</button>
    </div>
</div>

<style>
    .container{
        background-color: darkslategrey;
        height: 150px;
        width: 100vw;
        justify-content: center;
        align-items: center;
        vertical-align: middle;
    }
    h1{
        color: white;
    }
</style>

<!-- markup (zero or more items) goes here -->