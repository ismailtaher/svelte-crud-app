<script>
    export let task;
    import ProgressBar from "./ProgressBar.svelte"
</script>

<section style:border-left ="10px solid {task.color}">
    <h3>
        {task.title}
    </h3>
    <p>
        {task.content.slice(0,70)}...
    </p>
    <ProgressBar objectives={task.key_objectives}/>
</section>

<style>
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