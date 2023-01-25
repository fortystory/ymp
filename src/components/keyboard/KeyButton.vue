<!-- 每一个键盘按键 -->
<script>
export default {
//   props: ['title']
    data(){
        return {
            ispress:false,
            useIndex:1,
        }
    },
    props: ['keyname','wordroot'],
    methods:{
        press() {
            console.log($this.keyname)
            $this.isPress = true
        },
        up(){
            $this.isPress = false
        }
    }
}
</script>

<template>
    <div v-if="wordroot.empty"></div>
    <div v-else :id="'buttonShell_'+keyname" class="buttonShell">
        <div class="keyname">{{ keyname }}</div>
        <div class="symbol">
            <div class="single">
                <span v-for="(root,idx) in wordroot.single" :id="keyname+'_s_'+idx" class="character">{{ root }}</span>
            </div>
            <div class="wroot grown">
                <span v-for="(root,idx) in wordroot.grown" :id="keyname+'_g_'+idx" class="character">{{ root }}</span>
            </div>
            <div class="wroot part">
                <span v-for="(root,idx) in wordroot.part" :id="keyname+'_p_'+idx" class="character">{{ root }}</span>
            </div>
        </div>
    </div>
</template>

<style>
.buttonShell {
    display: grid;
    grid-template-columns: 1fr 4fr;
    /* border: 1px solid; */
    background-color: #282828;
    border-radius:5px;
}
.buttonShell:hover{
    transition: all .2s;
    transform: scale(1.5, 1.5);
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
    font-family: "更纱黑体 SC", xw_privateth;
}

.single {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    font-family: "更纱黑体 SC", xw_privateth;
    font-size: 2rem;
}

.character {
    justify-self: center;
}

.single>.character {
    grid-column: 1/4;
}
</style>