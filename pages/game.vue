<template>
  <div id="canvas">
    <div id="deep-space" />
    <div id="space-field">
      <SpaceObject id="spaceship" class="spaceship" :data="spaceField.ship" resolution="2" />

      <SpaceObject class="asteroid" :data="asteroid" resolution="2"
                  :key="asteroid.center"
                  v-for="asteroid in spaceField.asteroids" />

      <SpaceObject class="missile" :data="missile" resolution="2"
                  :key="missile.center"
                  v-for="missile in spaceField.missiles" />

      <SpaceObject class="explosion" :data="explosion" resolution="2"
                  :key="explosion.center"
                  v-for="explosion in spaceField.explosions" />
    </div>
  </div>
</template>

<script setup>
const {
  data: spaceField,
  refresh: updateSpaceField
} = await $get("/space-field");

onMounted(() => {
  window.addEventListener("keydown", async (event) => {
    const keyToCommand = {
      "ArrowUp": "MOVE_SHIP_UP",
      "ArrowDown": "MOVE_SHIP_DOWN",
      "ArrowRight": "MOVE_SHIP_RIGHT",
      "ArrowLeft": "MOVE_SHIP_LEFT",
      "Space": "LAUNCH_MISSILE",
      "Escape": "PAUSE_GAME",
    };

    const command = keyToCommand[event.code];

    // Ignore if invalid key was pressed
    if (command === undefined) return;

    console.log(`Triggering command: ${command}`);
    await $post("/ship/commands", { command })
  });

  window.setInterval(updateSpaceField, 20);
})
</script>

<style>
@keyframes slide {
  0% {
    transform: translate(1px);
  }
  50% {
    transform: translate(-1px);
  }
  100% {
    transform: translate(1px);
  }
}

#space-field {
  height: calc(100% - 4rem);
  width: calc(100% - 4rem);

  position: relative;
}

.spaceship {
  background-image: url("~/assets/spaceship.png");
}

.asteroid {
  background-image: url("~/assets/asteroid.png");
}

.missile {
  background-image: url("~/assets/missile.png");
}

.explosion {
  background-image: url("~/assets/explosion.png");
}
</style>