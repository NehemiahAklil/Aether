<script lang="ts" setup>
import { reactive } from 'vue'
import { Greet } from '../../wailsjs/go/main/App'
import { Icon } from '@iconify/vue';
import "@iconify-json/solar"

const data = reactive({
    name: "",
    resultText: "Please enter your name below 👇",
})

function greet() {
    Greet(data.name).then(result => {
        data.resultText = result
    })
}

</script>

<template>
    <main>
        <div id="result" class="result text-red-100">{{ data.resultText }}</div>
        <div class="text-gray-400">
            Text
        </div>
        <div id="input" class="input-box">
            <input id="name" v-model="data.name" autocomplete="off" class="input" type="text" />
            <button class="btn" @click="greet">Greet</button>
        </div>
        <div class="flex gap-4 p-4">
            <Icon icon="solar:home-2-linear" class="text-2xl text-blue-500" />

            <Icon icon="solar:settings-bold" class="text-2xl text-gray-700" />

            <Icon icon="solar:user-circle-bold-duotone" class="text-3xl text-indigo-600" />
        </div>
    </main>
</template>

<style scoped>
.result {
    height: 20px;
    line-height: 20px;
    margin: 1.5rem auto;
}

.input-box .btn {
    width: 60px;
    height: 30px;
    line-height: 30px;
    border-radius: 3px;
    border: none;
    margin: 0 0 0 20px;
    padding: 0 8px;
    cursor: pointer;
}

.input-box .btn:hover {
    background-image: linear-gradient(to top, #cfd9df 0%, #e2ebf0 100%);
    color: #333333;
}

.input-box .input {
    border: none;
    border-radius: 3px;
    outline: none;
    height: 30px;
    line-height: 30px;
    padding: 0 10px;
    background-color: rgba(240, 240, 240, 1);
    -webkit-font-smoothing: antialiased;
}

.input-box .input:hover {
    border: none;
    background-color: rgba(255, 255, 255, 1);
}

.input-box .input:focus {
    border: none;
    background-color: rgba(255, 255, 255, 1);
}
</style>
