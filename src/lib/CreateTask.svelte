<script>
    export let onAddTask;
    export let showModal = false;
    export let closeModal;

    let title = '';
    let content  = '';
    let dueDate = '';

    const handleSubmit = async (event) => {
        event.preventDefault();

        const newTask = {
            title,
            content,
            due_date: dueDate,
        };

        try {
            const response = await fetch ('http://localhost:3500/tasks', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(newTask),
            });

            if (response.ok) {
                const taskData = await response.json();
                onAddTask(taskData);
                closeModal();
                title='';
                content='';
                dueDate='';
                alert("Task Created Successfully");
            } else {
                const errorData = await response.json();
                alert(`Error: ${errorData.message}`);
            }
        } catch (error) {
            console.error("Error Submiting", error);
            alert("error occured while submitting");
        }
    }
  
  </script>
  
  {#if showModal}
  <div class="modal-overlay" on:click={closeModal}>
    <div class="modal-content" on:click|stopPropagation>
      <button class="close-btn" on:click={closeModal}>x</button>
      <h2>Create New Task</h2>
      <form on:submit={handleSubmit}>
        <label for="taskTitle">Title:</label>
        <input 
          type="text" 
          id="taskTitle" 
          name="taskTitle" 
          required 
          bind:value={title} 
        />

        <label for="taskContent">Content:</label>
        <textarea 
          id="taskContent" 
          name="taskContent" 
          required 
          bind:value={content}
        ></textarea>

        <label for="taskDueDate">Due Date:</label>
        <input 
          type="date" 
          id="taskDueDate" 
          name="taskDueDate" 
          required 
          bind:value={dueDate}
        />

        <button type="submit">Create Task</button>
      </form>
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
  
    form {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }
  
    input, textarea {
      padding: 0.5rem;
      font-size: 1rem;
    }
  </style>
  