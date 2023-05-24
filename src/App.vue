<template>
	<div class="container">
		<a @click="openWindow">Open window...</a>
	</div>
</template>

<script setup lang="ts">
import { WebviewWindow, type WindowOptions } from "@tauri-apps/api/window";

const openWindow = (e: MouseEvent) => {
  console.log(e)
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
