<template> 
	<div id="canvas">
		<table id="deep-space">
			<h1 class="title">
				PLACAR
			</h1>

			<tbody>
				<tr v-for="(player, idx) in three_best_players" :key="idx">
					<td class="leaderboard">{{ idx + 1 + "º:" }}</td>
					<td class="leaderboard">{{ player.score }}</td>
				</tr>
			</tbody>

			<NuxtLink to = "/" class = "link"> 
				VOLTAR AO MENU
			</NuxtLink>
		</table>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				players: [{
				  "startTime" : "2023-07-15T09:10:34.124354356",
				  "destroyedAsteroids" : 67,
				  "score" : 74560.0
				}, {
				  "startTime" : "2023-07-15T08:55:05.325547654",
				  "destroyedAsteroids" : 7,
				  "score" : 5200.0
				}, {
				  "startTime" : "2023-07-15T09:16:23.798193749",
				  "destroyedAsteroids" : 15,
				  "score" : 18700.0
				}, {
				  "startTime" : "2023-07-15T09:03:17.928754318",
				  "destroyedAsteroids" : 21,
				  "score" : 26300.0
				}]
			}
		},
		computed: {
		  three_best_players: function() {
				return this.players.slice().sort((a,b) => b.score - a.score).slice(0,3);
			}
		}
	};
</script>

<style>
.leaderboard {
	font-size: 80px;
	color: #E090DF;
}
</style>