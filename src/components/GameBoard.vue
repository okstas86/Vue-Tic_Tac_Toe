<template>
	<ol id="game-board">
		<li v-for="(row, rowIndex) in initialGameboard" :key="rowIndex">
			<ol>
				<li v-for="(playerSymbol, colIndex) in row" :key="colIndex">
					<button @click="() => handleSelectSquere(rowIndex, colIndex)">
						{{ playerSymbol }}
					</button>
				</li>
			</ol>
		</li>
	</ol>
</template>

<script setup>
import { ref, defineEmits } from 'vue'
const emit = defineEmits(['changeActivePlayer'])

const props = defineProps({})
const activePlayer = ref('')

const initialGameboard = ref([
	[null, null, null],
	[null, null, null],
	[null, null, null],
])

const gameBoard = ref(initialGameboard)

function handleSelectSquere(rowIndex, colIndex) {
	activePlayer.value = activePlayer.value === 'X' ? 'O' : 'X'

	gameBoard.value[rowIndex][colIndex] = activePlayer.value
	emit('changeActivePlayer', activePlayer.value)
}
</script>
