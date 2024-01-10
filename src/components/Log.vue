<template>
	<ol id="log">
		<li v-for="(item, index) in filteredLogItems" :key="index">
			{{ item.player }} selected {{ item.row }}, {{ item.col }}
		</li>
	</ol>
</template>

<script setup>
import { ref, defineProps, watchEffect, computed } from 'vue'

const props = defineProps({
	moveData: {
		type: Object,
		requared: true,
	},
})

const logItems = ref([])
watchEffect(() => {
	logItems.value.push(props.moveData)
})

const filteredLogItems = computed(() =>
	logItems.value.filter(item => item.player)
)
</script>
