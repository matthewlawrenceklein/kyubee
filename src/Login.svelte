<script>
    export let user 
</script>

<div class='main'>
    <div class='box'>
        <div class='container'>
            <button class='button primary' on:click={() => user.set(true)}>LOGIN</button>
        </div>
    </div>
</div>

<style>
    .main{
        width: 100vw;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        vertical-align: middle;
        background: #404040;
    }

    .box{
        background-color:#141414;
        height: 150px;
        width: 150px;
        display: flex;
        justify-content: center;
        align-items: center;
        vertical-align: middle;
    }

    

</style>

<!-- markup (zero or more items) goes here -->