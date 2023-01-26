<!-- 整个键盘布局 -->
<script>
import KeyButton from './KeyButton.vue'
import { keysStore } from '../../stores/keys'
// import { keysStore } from '../../stores/keys'

// const keyss = keysStore
// console.log(keyss)

export default {
  components: {
    KeyButton
  },
  data() {
    return {
        keys:keysStore()
    }
  },
  created(){
  },
//   mounted() {
//     for (let i = 0; i <  this.buttons.length; i++){
//         this.buttons[i].forEach(button => {
//             if(button.keyname == ''){
//                 return;
//             }
//             for (let j = 0; j <  button.wordroot.grown.length; j++){
//                 console.log(button.wordroot.grown[j]+":"+button.keyname+"_g_"+j);
//             }
//             for (let j = 0; j <  button.wordroot.part.length; j++){
//                 console.log(button.wordroot.part[j]+":"+button.keyname+"_p_"+j);
//             }
//             for (let j = 0; j <  button.wordroot.single.length; j++){
//                 console.log(button.wordroot.single[j]+":"+button.keyname+"_s_"+j);
//             }
//         });
//     }
//   }
}
</script>

<template>

    <div class="keyboard">
        <template v-for="line in keys.kmap">
            <div class="keyline">
                <template v-for="k in line">
                    <KeyButton
                    :emptykey="k==''"
                    :k="k"
                    :wr="keys.wt[k]"/>
                </template>
            </div>
        </template>
        <!-- <table>
            <tr>
                <td>1</td>
                <td>2</td>
            </tr>
            <tr>
                <td>3</td>
                <td>4</td>
            </tr>
            <tr>
                <td>5</td>
                <td>6</td>
            </tr>
        </table>
        <div style="font-size:2em;">
            <template v-for="(e,i) in keys.wk">
                {{ i }}
            </template>
        </div>
        <div>
            ------------
        </div>
        <div style="font-size:2em;font-family:TH-Tshyn-P0">
            <template v-for="(e,i) in keys.wk_old">
                {{ i }}
            </template>
        </div> -->
    </div>
</template>


<style>
.keyboard {
    display: grid;
    grid-template-columns: 1fr;
    font-family: "更纱黑体 SC", xw_privateth;
    font-size: 1rem;
    row-gap: 5px;
}

.keyline {
    display: grid;
    grid-template-rows: 8rem;
    gap: 5px;
    /* align-content: center; */
    justify-content: center;
}

.keyline:nth-child(1){
    grid-template-columns: repeat(10,8rem);
}
.keyline:nth-child(2){
    grid-template-columns: 4rem repeat(9,8rem) 4rem;
}
.keyline:nth-child(3){
    grid-template-columns: repeat(10,8rem);
}
</style>