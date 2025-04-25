<script>
    import ProgressBar from "./ProgressBar.svelte";
    import Modal from "./Modal.svelte";

    export let task;
    let showModal = false;

    const openModal = () => {
        showModal = true;
    };
</script>

<button class="task-card" on:click={openModal} aria-label="View task details" style:border-left= "10px solid {task.color}">
    <h3>{task.title}</h3>
    <p>{task.content.slice(0, 70)}...</p>
    <ProgressBar objectives={task.key_objectives}/>
    
    <Modal bind:showModal {task} />
</button>

<style>
    .task-card {
        background-color: #2b2b2b;
        padding: 1rem;
        min-height: 180px;
        border-radius: 10px;
        box-shadow: 0px 4px 6px rgba(255, 255, 255, 0.1);
        display: flex;
        flex-flow: column;
        justify-content: space-evenly;
        border: none;
        cursor: pointer;
        text-align: left;
    }

    .task-card h3 {
        margin-bottom: 0.5rem;
    }

    .task-card:focus {
        outline: none;
        border: 2px solid #4caf50;
    }
</style>