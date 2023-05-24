<template>
	<div class="container">
		{{ keyPressed }}
	</div>
</template>

<script setup lang="ts">
import { onMounted, onUnmounted, ref } from "vue";

const keyPressed = ref("n/a");
onMounted(() => {
	window.addEventListener("keydown", onKeyDown);
});
onUnmounted(() => {
	window.removeEventListener("keydown", onKeyDown);
});
const onKeyDown = (e: KeyboardEvent) => {
	keyPressed.value = e.code;
};
</script>

<style scoped></style>
