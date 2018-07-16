<template>
  <li class="tree-node list-unstyled">
    <div @click="toggleChildren">
      <span class="tree-node-icon" v-if="isFolder">
        <feather-icon :name="isFolderOpen ? 'folder-minus': 'folder-plus'"></feather-icon>
      </span>
      <span class="tree-node-label secondary-link">{{ model.name }}</span>
      <span v-if="model.data" class="tree-node-data pull-right text-muted">{{ model.data }}</span>
    </div>
    <ul class="tree-children" v-show="isFolderOpen" v-if="isFolder">
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
<style lang="scss">
.tree-node {
  cursor: pointer;
  margin: 2px 0;
}
.tree-children {
  padding-left: 1em;
  line-height: 1.5em;
}
.tree-node-icon {
  vertical-align: middle
}
</style>
