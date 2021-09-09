<script>
    import { Magic } from 'magic-sdk';
    const m = new Magic('pk_live_D76A8E4360817CD3'); // ✨

    export let user
    $: userEmail = ''

    const handleSignup = async() => {
        // log in a user by their email
        try {
        const user = await m.auth.loginWithMagicLink({ email: userEmail });
        console.log(user)
        } catch(err) {
            console.log(err)
        // Handle errors if required!
        }
    }
</script>

<div class='main'>
    <div class='box'>
        <div class='container'>
            <button class='button primary' on:click={() => user.set(true)}>LOGIN</button>
            <div class='row'>
                <input type='email' placeholder='email' bind:value={userEmail}>
                <button class='button primary' on:click={handleSignup}>sign up </button>
            </div>
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