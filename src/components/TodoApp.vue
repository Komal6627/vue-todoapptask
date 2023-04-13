<template>
  <div class="conatiner">
    <h2 class="text-center mt-5">Add Todo List</h2>
    <div class="d-flex">
      <input
        v-model="task"
        type="text"
        placeholder="Enter task"
        class="form-control m-2"
      />
      <button class="btn btn-success rounded-0" @click="submitTask">
        Submit
      </button>
    </div>

    <table class="table table-bordered">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Time</th>
          <th scope="col" class="text-center"></th>
          <th scope="col" class="text-center"></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <th>{{ task.name }}</th>
          <td>{{ task.time }}</td>
          <td class="text-center">
            <button class="btn btn-primary rounded-0" @click="editTask(index)">
              Edit
            </button>
          </td>
          <td class="text-center">
            <button class="btn btn-danger rounded-0" @click="deleteTask()">
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'TodoApp',
  props: {
    msg: String,
  },
  data() {
    return {
      task: '',
      editedTask: null,
      tasks: [],
    };
  },
  methods: {
    submitTask() {
      if (this.task.length === 0) return;
      if (this.editedTask === null) {
        this.tasks.push({
          name: this.task,
          time: '6:00',
        });
      } else {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }

      this.task = '';
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },
  },
};
</script>
