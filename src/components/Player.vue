<template>
	<li :class="!isActive ? 'active' : undefined">
		<span class="player">
			<span v-if="!isEditing" class="player-name">{{ playerName }}</span>
			<input v-else type="text" required v-model="playerName" />
			<span class="player-symbol">{{ symbol }}</span>
		</span>
		<button @click="handleEditClick">{{ isEditing ? 'Save' : 'Edit' }}</button>
	</li>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
	name: {
		type: String,
		requared: true,
	},
	symbol: {
		type: String,
		requared: true,
	},
	isActive: {
		type: Boolean,
		requared: true,
	},
})

let isEditing = ref(false)
let playerName = props.name

function handleEditClick() {
	isEditing.value = !isEditing.value
}
//
</script>
