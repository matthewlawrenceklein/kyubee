<script>
    import { onMount } from 'svelte'
    export let date;


    onMount(() => {
        console.log(date)
    });
</script>

<h3>{date.date}</h3>
<ul>
    <li>{date.title}</li>
    <li>{date.details}</li>
    {#each date.tags as tag}
         <li>{tag}</li>
    {/each}
</ul>

<style>
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->