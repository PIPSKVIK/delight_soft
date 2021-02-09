<template>
  <div id="app">
    <div class="container">
      <div class="container__body">
        <div class="container__info">
          <button @click="localFileInfo = null" class="container__info-button">
            clear info
          </button>
          <span>FILE INFORMATION</span>
          <ul v-for="(item, id) in localFileInfo" :key="id">
            <li>{{ item }}</li>
          </ul>
          <span></span>
        </div>
        <tree-browser :node="root" @onClick="nodelistener" />
        <iframe
          :src="storeName"
          width="600px"
          height="623px"
          frameborder="0"
        ></iframe>
      </div>
    </div>
  </div>
</template>

<script>
import TreeBrowser from "@/components/TreeBrowser";
export default {
  name: "App",
  components: { TreeBrowser },
  data() {
    return {
      storeName: "",
      root: {
        id: 5,
        parent_id: null,
        technical_acceptance_id: 11,
        name: "root",
        created_at: "2021-02-02 17:49:05",
        updated_at: "2021-02-02 17:49:05",
        under_folder: [
          {
            id: 1,
            parent_id: 1,
            technical_acceptance_id: 11,
            name: "pdf",
            created_at: "2021-02-02 17:49:05",
            updated_at: "2021-02-02 17:49:05",
            under_folder: [
              {
                id: 100,
                folder_id: 1,
                name: "first.pdf",
                store_name:
                  "https://zagorie.ru/upload/iblock/4ea/4eae10bf98dde4f7356ebef161d365d5.pdf",
                created_at: "2021-02-02 17:49:05",
                updated_at: "2021-02-02 17:49:05"
              },
              {
                id: 200,
                folder_id: 1,
                name: "second.pdf",
                store_name: "http://www.pdf995.com/samples/pdf.pdf",
                created_at: "2021-02-02 17:49:05",
                updated_at: "2021-02-02 17:49:05"
              }
            ]
          },
          {
            id: 2,
            parent_id: 2,
            technical_acceptance_id: 11,
            name: "pdff",
            created_at: "2021-02-02 17:49:05",
            updated_at: "2021-02-02 17:49:05",
            under_folder: [
              {
                id: 200,
                folder_id: 2,
                name: "Form Example.pdff",
                store_name:
                  "https://campustecnologicoalgeciras.es/wp-content/uploads/2017/07/OoPdfFormExample.pdf",
                created_at: "2021-04-04 11:49:05",
                updated_at: "2021-04-04 11:49:05"
              }
            ]
          },
          {
            id: 3,
            parent_id: 3,
            technical_acceptance_id: 11,
            name: "bmp",
            created_at: "2021-02-02 17:49:05",
            updated_at: "2021-02-02 17:49:05",
            under_folder: [
              {
                id: 300,
                folder_id: 3,
                name: "Youcone.bmp",
                store_name: "http://www.orimi.com/pdf-test.pdf",
                created_at: "2021-05-05 10:49:05",
                updated_at: "2021-05-05 10:49:05"
              }
            ]
          }
        ]
      },
      localFileInfo: null
    };
  },
  // mounted() {
  //   fetch("http://localhost:3000/root")
  //     .then(response => response.json())
  //     .then(json => {
  //       this.root = json;
  //     });
  // },
  methods: {
    nodelistener(node) {
      this.localFileInfo = node;
      this.storeName = node.store_name;
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
    width: 550px;
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
