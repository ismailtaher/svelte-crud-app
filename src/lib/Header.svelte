<script>
    export let onAddTask;
    import CreateTask from "./CreateTask.svelte";

    let showModal = false;
    const openCreateModal = () => {
        showModal= true;
    }
    const closeModal = () => {
        showModal = false;
    };
</script>

<header>
    <h1>
        <span>Svelte</span> crud
    </h1>
    <button on:click={openCreateModal}>
        Create Task
    </button>
</header>
<CreateTask showModal={showModal} closeModal={closeModal} onAddTask={onAddTask} />

<style>
    header {
        position: sticky;
        top: 0;
        width: 100%;
        font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
        padding: 1rem;
        display: flex;
        justify-content: space-between;
        align-items: center;
        border-bottom: 1px solid #ffffffde;
        background-color: #242424;
    }
    header span {
        color: #FF3E01;
    }
    button {
        padding: 0.6rem;
        border-radius: 10px;
        border: 1px solid #ffffffde;
        background-color: inherit;
        cursor: pointer;
    }

    button:hover {
        background-color: #FF3E01;
        border: 1px solid #FF3E01;
        transition: 300ms ease-in-out;
    }
</style>