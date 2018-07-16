<template>
  <li>
    <div
      class="tree-node"
      @click="toggleChildren">
      <span class="tree-node-icon" v-if="isFolder">
        <feather-icon :name="isFolderOpen ? 'folder-minus': 'folder-plus'"></feather-icon>
      </span>
      {{ model.name }}
    </div>
    <ul v-show="isFolderOpen" v-if="isFolder">
      <tree
        class="tree"
        v-for="(model, index) in model.children"
        :key="index"
        :model="model">
      </tree>
    </ul>
  </li>
</template>
<script>
export default {
  props: ['model'],
  computed: {
    isFolder: function() {
      return this.model.children && this.model.children.length;
    }
  },
  methods: {
    toggleChildren: function() {
      if (this.isFolder) {
        this.isFolderOpen = !this.isFolderOpen;
      }
    },
    addChild: function() {
      //
    }
  },
  data() {
    return {
      isFolderOpen: false,
    };
  }
};
</script>
<style scoped>
.item {
  cursor: pointer;
}
.bold {
  font-weight: bold;
}
ul {
  padding-left: 1em;
  line-height: 1.5em;
  list-style-type: dot;
}
li {
  list-style: none;
}
.tree-node-icon {
  vertical-align: middle
}
.tree-node{
  margin: 5px;
}
</style>
