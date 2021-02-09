<template>
  <div class="children">
    <div class="node" @click="nodeHeandler">
      <span class="node__folder" v-if="lastElement"
        >{{ localExpanded ? "&#128505;" : "&#65794;" }}
      </span>
      <span v-else>&#10022;</span>
      {{ node.name }}
    </div>
    <div v-if="localExpanded">
      <TreeBrowser
        v-for="child in node.under_folder"
        :key="child.id"
        :node="child"
        :expanded="childExpandedId === child.id"
        @update:expanded="handleUpdateChildExpanded(child.id, $event)"
        @onClick="node => $emit('onClick', node)"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "TreeBrowser",
  props: {
    node: Object,
    expanded: {
      type: Boolean,
      default: false
    }
  },

  data() {
    return {
      localExpanded: false,
      childExpandedId: null
    };
  },

  watch: {
    expanded: {
      immediate: true,
      handler(value) {
        this.localExpanded = value;
      }
    },
    localExpanded(value) {
      this.$emit("update:expanded", value);
    }
  },

  computed: {
    lastElement() {
      return this.node.under_folder;
    }
  },
  methods: {
    nodeHeandler() {
      this.localExpanded = !this.localExpanded;
      if (!this.lastElement) {
        this.$emit("onClick", this.node);
      }
    },
    handleUpdateChildExpanded(childId, value) {
      if (value) {
        this.childExpandedId = childId;
      } else if (childId === this.childExpandedId) {
        this.childExpandedId = null;
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
