<template>
	<main>
		<div id="game-container">
			{{ winner }}
			<ol id="players" class="highlight-player">
				<Player name="Player 1" symbol="X" :isActive="activePlayer === 'X'" />
				<Player name="Player 2" symbol="O" :isActive="activePlayer === 'O'" />
			</ol>
			<GameBoard @changeActivePlayer="handleActivePlayer" />
		</div>
		<Log :moveData="moveData" />
	</main>
</template>

<script setup>
import { ref } from 'vue'
import Player from './components/Player.vue'
import Log from './components/Log.vue'
import GameBoard from './components/GameBoard.vue'
import { WINNING_COMBINATIONS } from './winning-combinations'

const board = ref([])
const activePlayer = ref('O')
let moveData = ref({})
let winner = ref(null)

const handleActivePlayer = (newActivePlayer, row, col, gameBoard) => {
	activePlayer.value = newActivePlayer
	board.value = gameBoard

	checkForWinner()

	moveData.value = { player: newActivePlayer, row: row, col: col }
}

function checkForWinner() {
	for (const combination of WINNING_COMBINATIONS) {
		const firstSquareSimbol =
			board.value[combination[0].row][combination[0].column]
		const secondSquareSimbol =
			board.value[combination[1].row][combination[1].column]
		const thirdSquareSimbol =
			board.value[combination[2].row][combination[2].column]

		if (
			firstSquareSimbol &&
			firstSquareSimbol === secondSquareSimbol &&
			firstSquareSimbol === thirdSquareSimbol
		) {
			winner.value = firstSquareSimbol
		}
	}
}
</script>
