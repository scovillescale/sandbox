<template>
    <div class="wrapper">
        <container
            group-name="1"
            class="draggable-container"
            v-bind:get-child-payload="getChildPayload1"
            v-on:drop="onDrop('items1', $event)"
        >
            <draggable v-for="item in items1" v-bind:key="item.id">
                <div class="draggable-item" >{{ item.data }}</div>
            </draggable>

        </container>
        <container
            group-name="1"
            class="draggable-container"
            v-bind:get-child-payload="getChildPayload2"
            v-on:drop="onDrop('items2', $event)"
        >
            <draggable v-for="item in items2" v-bind:key="item.id">
                <div class="draggable-item" >{{ item.data }}</div>
            </draggable>

        </container>
    </div>
</template>

<script>
import { Container, Draggable } from "vue-smooth-dnd";
import { applyDrag } from "../utils/helpers";

export default {
    name: "Simple",
    components: { Container, Draggable },
    data() {
        return {
            items1: [
                {
                    id: 11,
                    data:'Draggable Item 1',
                },
                {
                    id: 12,
                    data:'Draggable Item 2',
                },
            ],
            items2: [],
        };
    },
    methods: {
        onDrop(collection, dropResult) {
            this[collection] = applyDrag(this[collection], dropResult);
        },
        getChildPayload1(index) {
            return this.items1[index];
        },
        getChildPayload2(index) {
            return this.items2[index];
        },
    },
};
</script>

<style>
    .wrapper {
        display: flex;
        justify-content: space-between;
    }
    .draggable-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        background: black;
        width: 300px;
        height: 300px;
    }
    .draggable-item {
        display: flex;
        flex-direction: column;
        justify-content: center;
        width: 300px;
        height: 100px;
        background: red;
        border: 1px solid #000;
    }
</style>