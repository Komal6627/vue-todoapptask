<template>
  <div class="conatiner">
    <h2>Todo List</h2>
    <div>
      <button class="btn btn-primary rounded-0 mx-1" @click="createFolder">
        Add Folder
      </button>

      <button class="btn btn-primary rounded-0 mx-1" @click="createList">
        Add List
      </button>
    </div>
    <div>
      <component v-bind:is="folderComponent"></component>
      <component v-bind:is="listComponent"></component>
    </div>
  </div>
</template>

<script>
import TodoApp from './TodoApp.vue';
import FolderAdd from './FolderAdd.vue';

export default {
  name: 'TodoAll',
  props: {
    msg: String,
  },
  components: {
    TodoApp,
    FolderAdd,
  },
  data() {
    return {
      listComponent: null,
      folderComponent: null,
    };
  },
  methods: {
    createList() {
      this.listComponent = 'TodoApp';
    },

    createFolder() {
      this.folderComponent = 'FolderAdd';
    },
  },
};
</script>
