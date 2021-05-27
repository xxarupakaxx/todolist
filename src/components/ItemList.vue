<template>
  <div>
    <div>ItemList</div>
    <div v-for="item in items" :key="item.name">
      <div class="item" :class="{ over500: item.price ==0 }">
        <div class="name">タスク: {{ item.name }}</div>
        <div class="price">{{ item.price }} 状態</div>
        <div v-if="item.price >= 2">最優先</div>
      </div>
    </div>
    <div>
      <label>
        タスク
        <input v-model="newItemName" type="text" />
      </label>
      <label>
        状態
        <input v-model="newItemPrice" type="number" />
      </label>
      <button @click="addItem">add</button>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const items = ref([
      { name: "起きる", price: 0 },
      { name: "歯を磨く", price: 1 },
    ]);
    const newItemName = ref("");
    const newItemPrice = ref(0);

    const addItem = () => {
      items.value.push({ name: newItemName.value, price: newItemPrice.value });
    };

    return { items, newItemName, newItemPrice, addItem };
  },
};
</script>
<style>
.over500 {
  color: red;
}
</style>