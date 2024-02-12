<template>
  <h1> Shopping List With Important Items</h1>
  <div id = 'container'>
    <form v-on:submit.prevent="addItem" class="fr">
      <p> what do you need :<br>
        <input type="text" placeholder="Enter item name " v-model="name">
      </p>
      <p>how many items : <br>
        <input type="number" min='0' placeholder="number of items..." v-model="number">
      </p>
      <p>
        <span>important?</span>
        <input type="checkbox" v-model="important">
        {{ important }}
      </p>
      <button type="submit">Add item</button>
    </form><br>
    <hr>
    <div>
      <strong> shopping list :-</strong>
      <ul>
        <li v-for="item in shoppingList" :key="item.name" style="font-size: x-large; background-color: aquamarine;">
          {{ item.name }} ({{ item.number }} items) - {{ item.important ? 'Important' : 'Not Important' }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { ref, reactive } from 'vue';

export default {
  setup() {
    const name = ref("");
    const number = ref(0);
    const important = ref(false);

    const shoppingList = reactive([]);

    function addItem() {
      shoppingList.push({
        name: name.value,
        number: number.value,
        important: important.value
      });

     
      name.value = "";
      number.value = 0;
      important.value = false;
    }

    return {
      name,
      number,
      important,
      shoppingList,
      addItem
    };
  }
}
</script>


<style scoped>
.fr{
  border-radius: 9px;
  max-width: 400px;
  margin: auto;
  padding: 20px;
  border: 3px solid grey;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: #5fb98c;
}
input{
  padding: 8px;
  margin-bottom: 10px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 4px;
}
h1{
  background-color: #6eadbd;
}

</style>
