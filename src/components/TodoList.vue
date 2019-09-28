<template>
  <div>
    <ul>
      <li v-for="(item, index) in todoItems" v-bind:key="index">
      {{item}}  
      <button @click="removeTodoItem(index,item)">remove</button>
      </li>
    </ul>
    <button v-on:click="fetchTodoItems">get all</button>
  </div>
</template>

<script>
export default {
	props: ['todoItems'],
	methods: {
		removeTodoItem: function(index, item) {
			this.$emit('removeTodoItems', index, item);
		},
		fetchTodoItems: function() {
			this.$emit('fetchTodoItems');
		},
	},
};
</script>
