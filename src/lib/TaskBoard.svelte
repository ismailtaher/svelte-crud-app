<script>
    import TaskCard from "./TaskCard.svelte";
    import { onMount } from "svelte";

    let tasks = []

    onMount(async () => {
        const res = await fetch('http://localhost:3500/tasks');
        tasks = await res.json();

        //sort tasks by objectives completion
        tasks.sort((a, b) => {
            const getCompletionPercentage = task => {
                const totalObjectives = task.key_objectives.length;
                const completedObjectives = task.key_objectives.filter(obj => obj.status === true).length;
                return totalObjectives > 0 ? (completedObjectives / totalObjectives) * 100 : 0;
            }
            return getCompletionPercentage(a) - getCompletionPercentage(b);
        })
        console.log(tasks)
    })
     
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