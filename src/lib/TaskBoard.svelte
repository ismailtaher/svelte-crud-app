<script>
    import TaskCard from "./TaskCard.svelte";
    export let tasks = []
     
</script>

<article>
        {#each tasks as task}
                <TaskCard task={task} />
        {/each}
</article>

<style>
    article {
        padding: 2rem;
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 2rem
    }
</style>