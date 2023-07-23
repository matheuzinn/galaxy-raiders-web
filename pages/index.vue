<template> 
	<div id="canvas">
		<div id="deep-space">
			<h1 class="title"> 
				GALAXY RAIDERS
			</h1>

			<NuxtLink to = "/game" class = "link"> 
        INICIAR PARTIDA
			</NuxtLink>

			<NuxtLink	to = "/leaderboard" class = "link"> 
				PLACAR 
			</NuxtLink>

			<NuxtLink to = "https://www.google.com" class = "link"> 
        SAIR
			</NuxtLink>
		</div>
	</div>
</template>

<style>
#canvas {
  height: calc(100vh - 4rem);
  width: calc(100vw - 4rem);
  padding: 2rem;
  background-color: #A44CD3;
  overflow: hidden;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}
#deep-space {
  height: calc(100% - 4rem);
  width: calc(100% - 4rem);
  background-image: url("~/assets/space.png");
  background-origin: content-box;
  animation: slide 3s linear infinite;
  position: absolute;
  z-index: 0;
  display: grid;
  place-items: center;
}
.link {
	display: flex;
	justify-content: center;
	align-items: center;

	height: 100px;
	width: 250px;

	font-size: 30px;
	font-weight: bold;

	background-color: transparent;
	color: #A44CD3;
	border: 3px solid #A44CD3;
	border-radius: 15px;

	cursor: pointer;
	text-align: center;
	text-decoration: none;
}

h1.title {
	font-size: 150px;
	color: #8800C7;
}
</style>