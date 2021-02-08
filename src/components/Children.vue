<template>
  <div class="children">
    <div class="node" @click="nodeHeandler">
      <span class="node__folder" v-if="lastElement"
        >{{ expanded ? "&#128505;" : "&#65794;" }}
      </span>
      <span v-else>&#10022;</span>
      {{ node.name }}
    </div>
    <div v-if="expanded">
      <TreeBrowser
        v-for="child in node.under_folder"
        :key="child.name"
        :node="child"
        @onClick="node => $emit('onClick', node)"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "TreeBrowser",
  props: {
    node: [Array, Object]
  },
  data() {
    return {
      expanded: false
    };
  },
  computed: {
    lastElement() {
      return this.node.under_folder;
    }
  },
  methods: {
    nodeHeandler() {
      this.expanded = !this.expanded;
      if (!this.lastElement) {
        this.$emit("onClick", this.node);
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.children {
  display: flex;
  margin-left: 10px;
}
.node {
  height: 40px;
  min-width: 100px;
  display: flex;
  align-items: center;
  font-size: 18px;
  cursor: pointer;
  color: #3fb984;
  margin-right: 20px;
  margin-bottom: 10px;
  border: 1px solid #3fb984;
  border-radius: 5px;

  &__folder {
    margin-right: 10px;
  }
}
</style>
