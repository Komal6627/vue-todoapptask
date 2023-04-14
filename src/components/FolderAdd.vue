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
      <button class="btn btn-warning rounded-0" @click="submitfolder">
        Submit
      </button>
    </div>
    <div>
      <ul
        class="list-group text-center"
        v-for="(folder, index) in folders"
        :key="index"
      >
        <div class="d-flex flex-row justify-content-center">
          <li class="list-group-item">
            <div @click="showList">
              <span class="fa-solid fa-folder" class="mx-1"></span
              >{{ folder.name }}
            </div>
            <component v-bind:is="listComponent"></component>
          </li>
          <div @click="editfolder(index)" class="m-2">
            <span class="fa fa-pen pointer"></span>
          </div>
          <div @click="deletefolder(index)" class="m-2">
            <span class="fa fa-trash pointer"></span>
          </div>
        </div>
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

      this.folder = ' ';
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
