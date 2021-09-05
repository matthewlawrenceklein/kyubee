<script>
    import { Button } from 'svelte-chota'
    export let user 
</script>

<Button on:click={() => user.set(null)}>LOG OUT</Button>

<style>
</style>

<!-- markup (zero or more items) goes here -->