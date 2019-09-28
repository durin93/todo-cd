<template>
  <div>
  <todo-header></todo-header>
  <todo-input v-on:add="addTodoItems"></todo-input>
  <todo-list 
  :todo-items="todoItems" 
  v-on:fetchTodoItems="fetchTodoItems" 
  @removeTodoItems="removeTodoItems"></todo-list>
  <todo-footer v-on:clear="clearTodoItems" @removeTodoItems="removeTodoItems"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
	data: function() {
		return {
			todoItems: [],
		};
	},
	components: {
		TodoHeader,
		// TodoInput: () => import('./components/TodoInput.vue')
		TodoInput: () => import('./components/TodoInput'),
		'todo-list': TodoList,
		'todo-footer': TodoFooter,
	},
	methods: {
		fetchTodoItems: function() {
			for (var i = 0; i < localStorage.length; i++) {
				this.todoItems.push(localStorage.key(i));
			}
		},
		clearTodoItems: function() {
			this.todoItems = [];
			localStorage.clear();
		},
		addTodoItems: function(value) {
			this.todoItems.push(value);
			localStorage.setItem(value, value);
		},
		removeTodoItems: function(index, item) {
			this.todoItems.splice(index, 1);
			localStorage.removeItem(item);
		},
	},
	created: function() {
		this.fetchTodoItems();
	},
};
</script>
