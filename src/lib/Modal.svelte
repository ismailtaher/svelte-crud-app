<script>
    export let showModal = false;
    export let task = null;
    
    // Function to close the modal
    const closeModal = () => {
      showModal = false;
    };
  </script>
  
  {#if showModal && task}
    <div class="modal-overlay" on:click={closeModal}>
        <div class="modal-content" on:click|stopPropagation>
            <button class="close-btn" on:click={closeModal}>x</button>
            <h2 id="modal-title">{task.title}</h2>
            <br>
            <p>{task.content}</p>
            <br>
            <p><strong>Due Date:</strong> {task.due_date}</p>
            <br>
            <p><strong>Status:</strong> {task.task_status}</p>
            <br>
            <ul>
                {#each task.key_objectives as obj}
                    <li>{obj.name} - {obj.status ? 'Completed' : 'Incomplete'}</li>
                {/each}
            </ul>
        </div>
    </div>
  {/if}
  
  <style>
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(0, 0, 0, 0.5);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }
  
    .modal-content {
        position: relative;
      background-color: black;
      padding: 2rem;
      border-radius: 10px;
      width: 50%;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }
  
    .close-btn {
        position: absolute;
        top: 10px;
        right: 10px;
      background-color: red;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      font-size: 16px;
      border-radius: 5px;
      cursor: pointer;
    }
  
    .close-btn:hover {
      background-color: darkred;
    }
  
    .modal-content h2 {
      margin-top: 0;
    }
  
    ul {
      list-style-type: none;
      padding: 0;
    }
  </style>