<template>
  <div id="app">
    <div class="container">
      <div class="container__body">
        <div class="container__info">
          <button @click="localFileInfo = []" class="container__info-button">
            clear info
          </button>
          <span>FILE INFORMATION</span>
          <ul v-for="(item, id) in localFileInfo" :key="id">
            <li>{{ item }}</li>
          </ul>
        </div>
        <tree-browser :node="root" @onClick="nodeHeandler" />
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
      root: {
        id: 5,
        parent_id: null,
        technical_acceptance_id: 11,
        name: "root",
        created_at: "2021-02-02 17:49:05",
        updated_at: "2021-02-02 17:49:05",
        under_folder: [
          {
            id: 6,
            parent_id: 5,
            technical_acceptance_id: 11,
            name: "excel",
            created_at: "2021-02-02 17:49:05",
            updated_at: "2021-02-02 17:49:05",
            under_folder: [
              {
                id: 100,
                folder_id: 1,
                name: "first.excel",
                store_name: "uYidnvrEkJ5tsjlCGpXU7qcjCdNiUX.xlsx",
                created_at: "2021-02-02 17:49:05",
                updated_at: "2021-02-02 17:49:05"
              },
              {
                id: 200,
                folder_id: 1,
                name: "second.excel",
                store_name: "uYidnvrEkJ5tsjlCGpXU7qcjCdNiUX.xlsx",
                created_at: "2021-02-02 17:49:05",
                updated_at: "2021-02-02 17:49:05"
              }
            ]
          },
          {
            id: 6,
            parent_id: 5,
            technical_acceptance_id: 11,
            name: "pdf",
            created_at: "2021-02-02 17:49:05",
            updated_at: "2021-02-02 17:49:05",
            under_folder: [
              {
                id: 200,
                folder_id: 2,
                name:
                  "\u0418\u043c\u043f\u043e\u0440\u0442_ 15.01\u00a0\u044f 3.xlsx",
                store_name: "qwdqwdqwdqwdqwdasdcwsddc.xlsx",
                created_at: "2021-04-04 11:49:05",
                updated_at: "2021-04-04 11:49:05"
              }
            ]
          },
          {
            id: 6,
            parent_id: 5,
            technical_acceptance_id: 11,
            name: "bmp",
            created_at: "2021-02-02 17:49:05",
            updated_at: "2021-02-02 17:49:05",
            under_folder: [
              {
                id: 300,
                folder_id: 3,
                name:
                  "\u0418\u043c\u043f\u043e\u0440\u0442_ 15.01\u00a0\u044f 3.xlsx",
                store_name: "uYidnvrEkJw.xlsx",
                created_at: "2021-05-05 10:49:05",
                updated_at: "2021-05-05 10:49:05"
              }
            ]
          }
        ]
      },
      localFileInfo: []
    };
  },
  // mounted() {
  //   fetch("http://localhost:3000/root")
  //     .then(response => response.json())
  //     .then(json => {
  //       this.files = json;
  //     });
  // },
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
