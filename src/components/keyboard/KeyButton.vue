<!-- 每一个键盘按键 -->
<script>
import { keysStore } from '../../stores/keys'

export default {
    props: ['emptykey','k','wr'],
    data() {
        return {
            keys:keysStore()
        }
    },
}
</script>

<template>
    <div v-if="emptykey"></div>
    <div v-else class="buttonShell" :class="{ highlight_button: keys.hk[k] }">
        <div class="keyname">{{ k }}</div>
        <div class="symbol">
            <div class="single">
                <span v-for="(root,idx) in wr.s" :class="{ highlight: keys.hw[root] }">{{ root }}</span>
            </div>
            <div class="wroot grown">
                <span v-for="(root,idx) in wr.g" :class="{ highlight: keys.hw[root] }">{{ root }}</span>
            </div>
            <div class="wroot part">
                <span v-for="(root,idx) in wr.p" :class="{ highlight: keys.hw[root] }">{{ root }}</span>
            </div>
        </div>
    </div>
</template>

<style>
.buttonShell {
    display: grid;
    grid-template-columns: 1fr 4fr;
    background-color: #282828;
    border-radius:5px;
}
.buttonShell:hover{
    transition: all .2s;
    transform: scale(2, 2);
    z-index:1000;
    background-color:rgb(0, 0, 0);
}

.keyname {
    font-size: 2rem;
    justify-self: center;
}

.wroot {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-auto-rows: 1.1rem;
}

.single {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    font-size: 2rem;
}

.grown{
    font-family: "更纱黑体 SC";
}

.part{
    font-family: xw_privateth,"更纱黑体 SC";
    margin-top:1rem;
}

.character {
    justify-self: center;
}

.single>.character {
    grid-column: 1/4;
}


.highlight{
  color:var(--color-green);
}
.highlight_button{
  background-color: hsla(159.6, 52.8%, 20.8%, 0.33);
}
</style>