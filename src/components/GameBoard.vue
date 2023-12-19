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
import { ref } from 'vue'

const initialGameboard = ref([
	[null, null, null],
	[null, null, null],
	[null, null, null],
])

const gameBoard = ref(initialGameboard)

function handleSelectSquere(rowIndex, colIndex) {
	gameBoard.value[rowIndex][colIndex] = 'X'
}
</script>
