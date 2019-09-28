<template>
  <div>
     <button @click="clearAllItems">clear all</button>
  </div>
</template>

<script>
export default {
	methods: {
		clearAllItems: function() {
			this.$emit('clear');
		},
	},
};
</script>
