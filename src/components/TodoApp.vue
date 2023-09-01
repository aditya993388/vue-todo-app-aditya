<template>
  <div class="container" style="max-width: 600px">
    <h2 class="text-center mt-5 text1">My Todo App</h2>

    <div class="d-flex mt-5">
      <input
        type="text"
        v-model="task"
        placeholder="Enter task"
        class="w-100 form-control"
      />
      <button class="btn btn-warning rounded-0 bga" @click="submitTask">
        SUBMIT
      </button>
    </div>

    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col" class="text1">Task</th>
          <th scope="col" class="text-center text1">Delete</th>
         
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
              <span class="fa fa-trash"></span>
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
          name: "Excercise for 1 hr"
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
.bga {
  background-color: indianred;
}
.text1 {
  color: brown;
}
</style>