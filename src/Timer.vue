<script setup>
import FocusMode from './components/FocusMode.vue'
import RestMode from './components/RestMode.vue'
import EditTimer from './components/EditTimer.vue'
import {ref} from 'vue'
const currentMode = ref('FocusMode')

const modes = {
    FocusMode,
    RestMode,
    EditTimer
}
</script>

<template>

    <div>
        <nav>
            <li @click="currentMode = 'FocusMode'">Focus</li>
            <li @click="currentMode = 'RestMode'">Rest</li>
            <li class="timer-setting" @click="currentMode = 'EditTimer'">Edit Timer</li>
        </nav>
        <main>
            <component :is="modes[currentMode]" />
        </main>
    </div>

</template>

<style lang="scss" scoped>
    div {
        background-color: white;
        height: fit-content;
        width: 40rem;
        border-radius: 7px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 4rem;
        nav {
            display: flex;
            list-style: none;
            justify-content: flex-start;
            width: 100%;
            padding-left: 3rem;
            .timer-setting {
                color: white;
                background-color: #262626;
                width: 7.5rem;
                &:hover {
                    background-color: burlywood;
                    color: black;
                }
            }
            li {
                background-color: white;
                padding: 0.5rem;
                width: 5rem;
                display: flex;
                align-items: center;
                justify-content: center;
                margin-right: 1rem;
                border-radius: 3px;
                user-select: none;
                border: 1px solid black;
                &:hover {
                    background-color: black;
                    color: white;
                    cursor: pointer;
                }
                &:active {
                    cursor: grabbing;
                    opacity: 0.7;
                }
            }
        }
        main {
            background-color: white;
            width: 100%;
            height: 20rem;
            border-radius: 5px;
        }
    }

    @media only screen and (max-width:425px) {
        div {
            padding: 0 1rem;
            height: 100vh;
            width: 100vw;
            nav {
                padding-left: 1rem;
                display: flex;
                align-items: center;
                justify-content: center;
            }
        }
    }
</style>