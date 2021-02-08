<template>
  <div id="app">
    <div class="container">
      <div class="container__body">
        <div class="container__info">
          <button @click="localFileInfo = []" class="container__info-button">clear info</button>
          <span>FILE INFORMATION</span>
          <ul v-for="(item, id) in localFileInfo" :key="id">
            <li>{{ item }}</li>
          </ul>
        </div>
        <tree-browser :node="files" @onClick="nodeHeandler"/>
      </div>
    </div>
  </div>
</template>

<script>
import TreeBrowser from "@/components/Children";
export default {
  name: "App",
  components: { TreeBrowser },
  data() {
    return {
      files: [],
      localFileInfo: []
    };
  },
  mounted() {
    fetch("http://localhost:3000/root")
      .then(response => response.json())
      .then(json => {
        this.files = json;
      });
  },
  methods: {
    nodeHeandler(node) {
      this.localFileInfo = node;
    }
  }
};
</script>

<style lang="scss">
#app {
  text-align: center;
  height: 100vh;
  background-color: #585858;
}
.container {
  &__body {
    display: flex;
    padding: 10px;
  }

  &__title {
    text-align: center;
  }

  &__info {
    color: white;
    background-color: gray;
    width: 400px;
    min-height: 200px;
    border-radius: 5px;
    position: relative;

    &-button {
      position: absolute;
      top: 10px;
      right: 10px;
    }

    & ul {
      text-align: left;
      list-style: none;
      margin: 0;
    }
    & li {
      margin-bottom: 10px;
    }
  }
}

body {
  margin: 0;
}
</style>
