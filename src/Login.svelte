<script>
    import { Button } from 'svelte-chota';
    export let user 
</script>

<Button on:click={() => user.set(true)}>LOGIN</Button>

<style>

</style>

<!-- markup (zero or more items) goes here -->