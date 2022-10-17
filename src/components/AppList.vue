<template>
  <div class="list-section">
    <ul class="list">
      <li
        class="list-item"
        v-for="item in items"
        :key="item.id"
        :class="{
          'list-item_picked': pickedItems.some((i) => i.id == item.id),
          'list-item_disabled': pickedItems.length >= limit && !pickedItems.some((i) => i.id == item.id)
        }"
      >
        <label class="list-item__label">
          <input
            type="checkbox"
            class="list-item__input"
            :value="item"
            v-model="pickedItems"
            :disabled="pickedItems.length >= limit && !pickedItems.some((i) => i.id == item.id)"
          />
          <p class="list-item__text">{{ item.name }}</p>
        </label>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: true
    },
    limit: {
      type: Number,
      required: true
    }
  },
  emits: ["pickItem"],
  data() {
    return {
      pickedItems: []
    };
  },
  watch: {
    pickedItems(to) {
      this.$emit("pickItem", to);
    }
  }
};
</script>

<style scoped>
.list-section {
  width: 45%;
  border: 2px solid #000;
  padding: 20px;
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
  cursor: pointer;
}
.list-item_picked {
  border: 1px solid tomato;
  color: tomato;
}
.list-item_disabled {
  opacity: 0.5;
  cursor: default;
}
.list-item__label {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: inherit;
}
</style>
