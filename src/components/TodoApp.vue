<template>
  <div class="container" id="my-todo-app">
    <h2 class="text-center mt-5 custom-text">My Todo App</h2>

    <div class="d-flex mt-5">
      <input
        type="text"
        v-model="task"
        placeholder="Enter task"
        class="w-100 custom-input"
      />
      <button class="custom-button" @click="submitTask">
        SUBMIT
      </button>
    </div>

    <table class="custom-table mt-5">
      <thead>
        <tr>
          <th scope="col" class="custom-text">Task</th>
          <th scope="col" class="text-center custom-text">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>
            <span>
              {{ task.name }}
            </span>
          </td>
          <td class="text-center">
            <div @click="deleteTask(index)">
              <span class="custom-icon">&#x1F5D1;</span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },

  data() {
    return {
      task: "",

      tasks: [
        {
          name: "Buy apples from the supermarket." 
        },
        {
          name: "Exercise for 1 hr"
        },
        {
          name: "Complete homework."
        },
      ],
    };
  },

  methods: {
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },

    submitTask() {
      if (this.task.length === 0) return;

        this.tasks.push({
          name: this.task,
        });

      this.task = "";
    },
  },
};
</script>

<style scoped>
#my-todo-app {
  max-width: 650px;
}

.custom-text {
  color: brown;
}

.custom-input {
  width: 100%;
}

.custom-button {
  background-color: indianred;
  border: none;
  border-radius: 0;
  padding: 10px 20px;
  cursor: pointer;
}

.custom-table {
  border: 1px solid #ccc;
  width: 100%;
}

.custom-icon {
  font-size: 24px;
  cursor: pointer;
}
</style>
