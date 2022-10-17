<template>
  <div class="head-section">
    <ul class="list">
      <li class="list-item" v-for="item in result" :key="item.id">
        {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    result: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.head-section {
  width: 45%;
  border: 2px solid #000;
  padding: 20px;
  min-height: 70px;
}

.list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.list-item {
  border: 1px solid #000;
  width: 45%;
  margin-bottom: 10px;
  padding: 10px;
  font-size: 16px;
  font-weight: 600;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
