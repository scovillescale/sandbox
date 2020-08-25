<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.png" />
        <drag-and-drop />
    </div>
</template>

<script>
import DragAndDrop from "./components/DragAndDrop";
import DragGroups from "./components/DragGroups";

export default {
    name: "app",
    components: {
        DragAndDrop,
        DragGroups,
    },
};
</script>

<style>
#app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
