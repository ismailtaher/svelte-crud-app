<script>
    import ProgressBar from "./ProgressBar.svelte";
    import { onMount } from "svelte";

    let tasks = []

    onMount(async () => {
        const res = await fetch('http://localhost:3500/tasks');
        tasks = await res.json();
        console.log(tasks)
    })
     
</script>

<article>
        {#each tasks as task}
                <section style:border-left ="10px solid {task.color}">
                    <h3>
                        {task.title}
                    </h3>
                    <p>
                        {task.content.slice(0,70)}...
                    </p>
                    <ProgressBar objectives={task.key_objectives}/>
                </section>
        {/each}
</article>

<style>
    article {
        padding: 2rem;
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 2rem
    }

    section {
        background-color: #2b2b2b;
        padding: 1rem;
        min-height: 180px;
        border-radius: 10px;
        box-shadow: 0px 4px 6px rgba(255, 255, 255, 0.1);
        display: flex;
        flex-flow: column;
        justify-content: space-evenly;
    }

    section h3 {
        margin-bottom: 0.5rem;
    }
</style>