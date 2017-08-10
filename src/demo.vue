<template>
	<div class="demo">
		<draggable
			class="pull"
			:nodes="nodes"
		></draggable>
	</div>
</template>

<script>
	import draggable from './draggable.vue';
	import {nodes1} from './config';

	export default {
		name: 'demo',

		data() {
			return {
				nodes: nodes1
			};
		},

		components: {
			draggable
		}
	};
</script>

<style>
	.pull{
		margin: 20px;
	}
</style>