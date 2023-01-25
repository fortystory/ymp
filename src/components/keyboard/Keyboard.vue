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
        buttons:[
            [
                {keyname:"Q",wordroot:{empty:false,single:[],grown:["革","臣","因","旦","今","令","丘","斤","六","米","民","叚"],part:["","朿","","𢦏","亼","冖","㐫","㡀"],}},
                {keyname:"W",wordroot:{empty:false,single:[],grown:["去","求","万","日","曰","我","毛","川","象","曾","力","乃"],part:["⺀","冫","丷","","","","","","彡","","巛","","卩",],}},
                {keyname:"E",wordroot:{empty:false,grown:[],part:[],single:["⼀"]}},
                {keyname:"R",wordroot:{empty:false,grown:[],single:["⼂"],part:["辶","廴",]}},
                {keyname:"T",wordroot:{empty:false,single:[],grown:["才","木","西","酉","此","占","用","鼠","久","臼","户","加","甬",],part:["乛","㇕","㇆","","㇉","㇡","","","","",],}},
                {keyname:"Y",wordroot:{empty:false,single:[],grown:["而","二","莫","辰","车","井","耳","堇","山","巾","化","缶","瓜","爪","麻","兼","习","羽",],part:["","","爫","","癶","","","阝","","",],}},
                {keyname:"U",wordroot:{empty:false,grown:[],part:[],single:["ㄋ"],}},
                {keyname:"I",wordroot:{empty:false,grown:[],part:[],single:["⼁"],}},
                {keyname:"O",wordroot:{empty:false,grown:[],part:[],single:["⼃"],}},
                {keyname:"P",wordroot:{empty:false,single:[],grown:["三","十","犬","尧","共","雨","食","舟","卯","定","次","火","亦","乙","幺"],part:["","龷","","","犭","饣","","","","","","","乚",],}},
            ],[
                {keyname:"",wordroot:{empty:true},},
                {keyname:"A",wordroot:{empty:false,single:[],grown:["于","亍","丁","厂","牙","由","曲","甲","几","仑","尔","欠","前","广","马","丑",],part:["","","","","",""],}},
                {keyname:"S",wordroot:{empty:false,single:[],grown:["王","是","亚","示","呆","分","壬","鬼","及","言","子","孑","聿","刀","凵",],part:["","冂","","讠","屰","",],}},
                {keyname:"D",wordroot:{empty:false,single:[],grown:["石","未","末","耒","甘","廿","执","贝","虍","人","入","白","鱼","卑","豸","殳","酋","穴","也","糸",],part:["","","","","","","",],}},
                {keyname:"F",wordroot:{empty:false,single:[],grown:["天","者","甫","见","从","夭","彳","八","鸟","门","又","双",],part:["艹","","","","",""],}},
                {keyname:"G",wordroot:{empty:false,single:[],grown:["可","其","至","里","田","畀","生","先","段","九","已","己","巴","巳",],part:["扌","","","",],}},
                {keyname:"H",wordroot:{empty:false,single:[],grown:["不","青","直","面","平","圭","豆","豕","止","齿","凹","凸","光","月","立","角","立","单",],part:["忄","礻","衤","","","","","","","","厃",""],}},
                {keyname:"J",wordroot:{empty:false,single:[],grown:["一","夫","五","丌","瓦","韦","寸","业","自","告","勿","衣","半",],part:["","","亻","","","","㇐","㇑","㇔","㇓"],}},
                {keyname:"K",wordroot:{empty:false,single:[],grown:["大","正","戊","弋","戈","戋","敖","口","囗","片","之","主","羊","尺",],part:["爿","","","","","","","",],}},
                {keyname:"L",wordroot:{empty:false,single:[],grown:["下","元","工","龙","士","土","鬲","上","卜","内","父","竹","心","京","农",],part:["𥫗","𡗗","龹","疒","⽱","","","","","","","",],}},
                {keyname:"",wordroot:{empty:true},},
            ],[
                {keyname:"",wordroot:{empty:true},},
                {keyname:"Z",wordroot:{empty:false,single:[],grown:["束","非","北","身","垂","各","乍","皮","尸",],part:["","","","丬",],}},
                {keyname:"X",wordroot:{empty:false,single:[],grown:["丰","尢","回","黑","儿","刍","弟","亡","发","弓",],part:["","","","","纟","","𠂔","",],}},
                {keyname:"C",wordroot:{empty:false,single:[],grown:["丽","赤","小","四","皿","公","牛","合","禾","了","尹","奴",],part:["彐","罒","","","","","","","","牜","厶",""],}},
                {keyname:"V",wordroot:{empty:false,single:[],grown:["相","古","中","少","气","矢","金","母","毋","毌",],part:["匚","コ","","","","钅","宀",],}},
                {keyname:"B",wordroot:{empty:false,single:[],grown:["更","髟","歹","屯","目","且","虫","长","代","乎","争","夕","以","辟",],part:["","","","","","","",""],}},
                {keyname:"N",wordroot:{empty:false,single:[],grown:["开","干","吉","页","七","廾","水","手","千","匕","舌","文","义","辛",],part:["","","","氵","","灬","","","","刂","","夂","","","","","",],}},
                {keyname:"M",wordroot:{empty:false,single:[],grown:["走","云","林","区","比","折","骨","氏","隹","方","音","鹿","女",],part:["疋","","龰","","",],}},
                {keyname:"",wordroot:{empty:true},},
                {keyname:"",wordroot:{empty:true},},
            ]
        ],
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
        <div class="keyline" v-for="line in buttons">
            <KeyButton v-for="botton in line" :keyname="botton.keyname" :wordroot="botton.wordroot" />
        </div>
    </div>
    <div>

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
    grid-template-rows: 7rem;
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