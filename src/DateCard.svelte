<script>
    import { onMount } from 'svelte'
    export let date;


    onMount(() => {
    });
</script>

<div class='container card'>
    <header class='heading'>
        <h3>{date.date}</h3>
    </header>
    <ul>
        <li>{date.title}</li>
        <!-- <li>{date.details}</li> -->
        {#if date.tags}
             {#each date.tags as tag}
                  <li><strong>{tag}</strong></li>
             {/each}
        {/if}
    </ul>
</div>

<style>
    .card {
        width: 280px;
        margin: 10px;
        margin-top: 20px;
    }
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->