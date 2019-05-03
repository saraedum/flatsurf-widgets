<template>
	<extended-click-area @click="$emit('click')" @mouseenter="$emit('mouseenter')" @mouseleave="$emit('mouseleave')">
		<line class="half-edge" :x1="edge.ps.x" :y1="edge.ps.y" :x2="edge.pe.x" :y2="edge.pe.y" />
	</extended-click-area>
</template>
<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";
import Flatten from "@flatten-js/core";

import ExtendedClickArea from "../Shared/ExtendedClickArea.vue";

@Component({
	components: { ExtendedClickArea },
})
export default class HalfEdge extends Vue {
	@Prop({required: true, type: Object}) edge!: Flatten.Segment;
}
</script>
<style lang="scss">
.flatsurf {
	.highlight line {
		stroke: green;
		stroke-width: 2px;
		cursor: pointer;
	}

	.selected line {
		stroke: red;
		stroke-width: 4px;
		stroke-dasharray: 10;
		animation: dash 250ms linear;
	}
}

@keyframes dash {
	to { stroke-dashoffset: 25; }
}
</style>