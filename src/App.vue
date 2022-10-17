<template>
  <header class="header">
    <AppHead :result="result1" v-if="result1.length" />
    <AppHead :result="result2" v-if="result2.length" />
  </header>
  <main class="main">
    <AppList :items="items1" :limit="6" @pickItem="pickItem($event, 1)" />
    <AppList :items="items2" :limit="1" @pickItem="pickItem($event, 2)" />
  </main>
</template>

<script>
import AppHead from "./components/AppHead.vue";
import AppList from "./components/AppList.vue";
import { ref } from "vue";

export default {
  components: {
    AppHead,
    AppList
  },

  setup() {
    const items1 = [
      {
        id: 1,
        name: "Shoes 1"
      },
      {
        id: 2,
        name: "Shoes 2"
      },
      {
        id: 3,
        name: "Shoes 3"
      },
      {
        id: 4,
        name: "Shoes 4"
      },
      {
        id: 5,
        name: "T-shirt 1"
      },
      {
        id: 6,
        name: "T-shirt 2"
      },
      {
        id: 7,
        name: "T-shirt 3"
      },
      {
        id: 8,
        name: "T-shirt 4"
      }
    ];

    const items2 = [
      {
        id: 11,
        name: "Jacket 1"
      },
      {
        id: 12,
        name: "Jacket 2"
      },
      {
        id: 13,
        name: "Jacket 3"
      },
      {
        id: 14,
        name: "Jacket 4"
      },
      {
        id: 15,
        name: "Hoodie 1"
      },
      {
        id: 16,
        name: "Hoodie 2"
      },
      {
        id: 17,
        name: "Hoodie 3"
      },
      {
        id: 18,
        name: "Hoodie 4"
      }
    ];

    let result1 = ref([]);
    let result2 = ref([]);

    const pickItem = (items, arr) => {
      arr === 1 ? (result1.value = items) : (result2.value = items);
    };

    return { items1, items2, result1, result2, pickItem };
  }
};
</script>

<style>
*,
::before,
::after {
  box-sizing: border-box;
}

input {
  visibility: hidden;
  position: absolute;
  position: absolute;
  height: 0;
  width: 0;
  outline: none;
  z-index: -1;
  margin: 0;
  padding: 0;
}
ul,
ol {
  padding: 0;
  margin: 0;
  list-style-type: none;
}
.header {
  margin-bottom: 40px;
}
.header,
.main {
  display: flex;
  justify-content: space-between;
}
</style>
