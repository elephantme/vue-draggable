<template>
	<div class="dk-container" :style="{'height': containerHeight + 'px'}">
		<div 
			class="dk-item" 
			v-for="(node, index) of nodes"
			:style="getStyle(index)"
			:key="node.id"
		>
			<div class="dk-item-content">{{node.name}}</div>
		</div>
	</div>
</template>

<script>
	import {config} from './config';

	export default {
		name: 'draggable',
		props: {
			nodes: {
				type: Array
			}
		},

		computed: {
			cfg() {
				return Object.assign({}, config);
			},

			containerHeight() {
				if(this.nodes == null || this.nodes.length === 0) return 0;
				return this.nodes.length * this.cfg.nodeH + (this.nodes.length - 1) * this.cfg.padding;
			}
		},

		methods: {
			getStyle(index) {
				console.log(index)
				return {
					transform: "translate(0px, "+ ((this.cfg.nodeH + this.cfg.padding) * index) +"px)"
				};
			}
		}
	};
</script>

<style>
	.dk-container{
		position: relative;
		width: 200px;
		border: 1px solid #ccc;
	}
	.dk-item{
		position: absolute;
		height: 26px;
		max-width: 180px;
	}
	.dk-item-content{
		border-radius: 13px;
	    color: #fff;
	    background-color: #aac814;
	    padding: 0 14px;
	    line-height: 26px;
	}
</style>