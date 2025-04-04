<script setup>
import {ref, computed, onMounted} from 'vue'

const MINUTE = 60000
const SECOND = 1000

const min = ref(24)
const sec = ref(60)

const resetTimer = () => {
    min.value = 25
    sec.value = 0
}

const timer = () => {
    const timerInterval = setInterval(() => {
        if(sec.value>0){
            sec.value--
        } else {
            if(min.value>0){
                min.value--
                sec.value=59
            } else {
                resetTimer()
                clearInterval(timerInterval)
            }
        }
    }, SECOND);
}
</script>

<template>

    <div class="main-container">
        <h1 class="timer">{{ min }} : {{ sec }}</h1>
        <div>
            <button @click="timer">Start Timer</button>
            <button @click="resetTimer" class="reset-btn">Reset Timer</button>
        </div>
    </div>

</template>

<style lang="scss" scoped>
.main-container {
    width: 100%;
    height: 100%;
    padding: 0;
    h1 {
        background-color: white;
        height: 13rem;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 8rem;
        border: 1px solid black;
        border-radius: 5px 5px 0 0;
    }
    div {
        width: 100%;
        .reset-btn {
            border-radius: 0 0 5px 0;
            &:hover {
                background-color: burlywood;
            }
        }
        button {
            margin-top: 0.3rem;
            background-color: #262626;
            height: 4rem;
            width: 50%;
            font-size: 1rem;
            color: white;
            border: solid 1px #262626;
            border-radius: 0 0 0 5px;
            &:hover {
                background-color: burlywood;
                color: black;
                cursor: pointer;
            }
            &:active {
                cursor: grabbing;
                opacity: 0.7;
            }
        }
    }
    
}

@media only screen and (max-width:425px) {
    .main-container {
        h1 {
            font-size: 5.5rem;
        }
    }        
}
</style>