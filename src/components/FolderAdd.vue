<template>
  <div class="conatiner">
    <h2 class="text-center mt-5">Add Folder for List</h2>
    <div class="d-flex">
      <input
        v-model="folder"
        type="text"
        placeholder="Enter folder"
        class="form-control m-2"
      />
      <button class="btn btn-success rounded-0" @click="submitfolder">
        Submit
      </button>
    </div>
    <div>
      <ul class="list-group" v-for="(folder, index) in folders" :key="index">
        <li class="list-group-item">
          <!-- <font-awesome-icon icon="fa-solid fa-folder" /> -->
          <button btn btn-success @click="showList">{{ folder.name }}</button>
          <component v-bind:is="listComponent"></component>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import TodoApp from './TodoApp.vue';
export default {
  name: 'FolderAdd',
  props: {
    msg: String,
  },
  components: {
    TodoApp,
  },
  data() {
    return {
      listComponent: null,
      folder: '',
      editedFolder: null,
      folders: [],
    };
  },
  methods: {
    submitfolder() {
      if (this.folder.length === 0) return;
      if (this.editedFolder === null) {
        this.folders.push({
          name: this.folder,
        });
      } else {
        this.folders[this.editedFolders].name = this.folder;
        this.editedFolder = null;
      }

      this.folder = '';
    },
    deletefolder(index) {
      this.folders.splice(index, 1);
    },
    editfolder(index) {
      this.folder = this.folders[index].name;
      this.editedfolder = index;
    },
    showList() {
      this.listComponent = 'TodoApp';
    },
  },
};
</script>
