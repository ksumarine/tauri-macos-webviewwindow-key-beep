<template>
	<div class="container">
		{{ keyPressed }}
		<a @click="openWindow">Open window...</a>
	</div>
</template>

<script setup lang="ts">
import { WebviewWindow, type WindowOptions } from "@tauri-apps/api/window";
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
const openWindow = (e: MouseEvent) => {
	console.log(e);
	const options: WindowOptions = {
		url: "secondary.html",
		title: "Another window...",
		focus: true,
		resizable: true,
		alwaysOnTop: true,
		width: 400,
		height: 300,
		x: 0,
		y: 100,
	};
	// open the window
	new WebviewWindow("anotherWindow", options);
};
</script>

<style scoped>
a {
	cursor: pointer;
}
</style>
