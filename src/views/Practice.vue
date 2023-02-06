<!-- 整个键盘布局 -->
<script>
// import { ref, watch } from 'vue'
import Keyboard from '../components/keyboard/Keyboard.vue'
// import Toggle from '../components/ui/Toggle.vue'
import { keysStore } from '../stores/keys'

export default {
  components: {
    Keyboard
  },
  data() {
    return {
      croots:[],
      currentinput:'',
      lastinput:'',
      lastHighlight:'',
      practice_type:'wt_all',
      split:[],
      split_key:[],
      keys:keysStore(),
      erio:["E","R","I","O"],//前两个字根不会出现这些按键 U也不会出现,但U没有和J重复的字根
      spr:["辶","廴"],//特殊处理这两个字根
    }
  },
  methods:{
    //获取字根或汉字并打乱顺序
    getrandomroots:function(){
      this.croots = this.shuffle(this.keys[this.practice_type])//更新练习字根或汉字
      // this.croots = ["","⻊","","丬"];
      if(this.practice_type == 'character'){//如果是汉字练习,会有多个字根
        // this.croots = ["辟","这","我"];
        this.split_root();
      }
    },
    inputcheck:function(){
      if(this.practice_type != 'character'){//字根练习
        // 判断是否输入正确 当前输入是否等于字根对应的按键
        if(this.currentinput.toUpperCase() == this.keys.wk[this.croots[0]]){
          this.croots.shift()//移除数组第一个元素
          if(this.keys.tips){
            this.highlight()
          }
        }
      }else{//汉字练习
        if(this.currentinput.toUpperCase() == this.split_key[0]){
          let tk = this.split_key.shift()//移除数组第一个元素 按键
          let tw = this.split.shift()//移除数组第一个元素 字根
          this.keys.hk[tk] = false
          this.keys.hw[tw] = false
          if(this.keys.tips){
            this.highlight()
          }
          if(this.split.length == 0 && this.croots.length > 0){
            this.croots.shift()//移除数组第一个元素
            this.split_root()
          }
        }
      }
      this.lastinput = this.currentinput.toUpperCase()
      this.currentinput = ''
    },
    highlight:function(){//刷新高亮提示
      if(!this.keys.tips){
        return
      }
      //去掉之前的高亮
      this.keys.lhk.forEach(lhke => {
        this.keys.hk[lhke] = false
      });
      this.keys.lhw.forEach(lhwe => {
        this.keys.hw[lhwe] = false
      });
      //更新样式
      if(this.practice_type != 'character'){
        this.keys.hk[this.keys.wk[this.croots[0]]] = true
        this.keys.hw[this.croots[0]] = true
        this.keys.lhk = [this.keys.wk[this.croots[0]]]
        this.keys.lhw = [this.croots[0]]
      }else{
        this.keys.lhk = [];
        this.keys.lhw = [];
        this.split.forEach(sr => {
          let tk = this.keys.wk[sr]
          if(this.erio.includes(tk) && !this.spr.includes(sr)){
            tk = "J"
          }
          this.keys.hk[tk] = true
          this.keys.hw[sr] = true
          this.keys.lhk.push(tk)
          this.keys.lhw.push(sr)
        });
      }
    },
    change_practice_type:function(){
      this.getrandomroots()
      this.highlight()//刷新高亮
    },
    //乱序数组,洗牌算法
    shuffle:function(arr) {
      let len = arr.length;
      while (len) {
        let random_inx = Math.floor(Math.random() * len--);
        [arr[random_inx], arr[len]] = [arr[len], arr[random_inx]];
      }
      return arr;
    },
    toggle:function(){//开关提示
      this.keys.tips = !this.keys.tips
      if(this.keys.tips){
        this.highlight()
      }else{
        this.keys.lhw.forEach(lhwe => {
          this.keys.hw[lhwe] = false
        });
        this.keys.lhk.forEach(lhke => {
          this.keys.hk[lhke] = false
        });
      }
    },
    split_root:function(){
      if(this.croots.length <= 0){
        return
      }
      //字根拆分提示
      this.split = [this.keys.dic[this.croots[0]][0],this.keys.dic[this.croots[0]][1]]
      this.split_key = [this.keys.wk[this.split[0]],this.keys.wk[this.split[1]]]
      //处理笔画，第二个字根不会是euio
      if(this.erio.includes(this.split_key[0]) && !this.spr.includes(this.split[0])){
        this.split_key[0] = "J"
      }
      if(this.erio.includes(this.split_key[1]) && !this.spr.includes(this.split[1])){
        this.split_key[1] = "J"
      }
      this.highlight()
    }
  },
  mounted(){
    this.getrandomroots()
    this.highlight()
  },
  unmounted(){
    //还原样式
    Object.keys(this.keys.hk).forEach((key) => {
      this.keys.hk[key] = false
    })
    Object.keys(this.keys.hw).forEach((key) => {
      this.keys.hw[key] = false
    })
  },
}
</script>

<template>
  <div class="practice">
    <div class="kboard">
      <Keyboard />
    </div>
    <!-- 配置开关 -->
    <!-- practice_input -->
    <div class="practice_type">
      <label for="wt_grown">
        <input type="radio" id="wt_grown" value="wt_grown" v-model="practice_type" @change="change_practice_type" />
        <span>成字根练习</span>
      </label>
      <label for="wt_part">
        <input type="radio" id="wt_part" value="wt_part" v-model="practice_type" @change="change_practice_type" />
        <span>部件字根练习</span>
      </label>
      <label for="wt">
        <input type="radio" id="wt" value="wt_all" v-model="practice_type" @change="change_practice_type" />
        <span>全部字根练习</span>
      </label>
      <label for="character">
        <input type="radio" id="character" value="character" v-model="practice_type" @change="change_practice_type" />
        <span>常用字练习</span>
      </label>
      <input type="button" :value="keys.tips ? '已开启提示' : '已关闭提示'" @click="toggle()" class="toggle" :class="{ toggle_off:!keys.tips }"/>
    </div>
    <div class="wrtext">
      <span v-for="r in this.croots">{{ r }}</span>
    </div>
    <div class="practice_input">
      <div>
        <!--拆分汉字列表-->
        <span class="split" v-show="practice_type == 'character'">
          <span v-for="rs in split"> {{ rs }} </span>
        </span>
        <span class="lastinput">{{ lastinput }}</span>
        <input type="text" class="practice_input_box" v-model="currentinput" v-on:input="inputcheck()">
      </div>
    </div>
    <!-- <div class="show_input"> -->
      <!-- 输入提示 -->
      <!-- show_input -->
    <!-- </div> -->
  </div>
</template>


<style>
.practice{
  display:grid;
  grid-template-rows: 25rem 3rem 11rem 6rem;
}
.wrtext{
  border-width: 10px;
  border-style: solid;
  border-radius: 40px;
  padding-left: 20px;
  font-size: 5rem;
  border-color: #282828;
  margin-top: 10px;
  margin-bottom: 10px;
  background-color: #202020;
  height: 9rem;
  overflow: hidden;
  font-family: "更纱黑体 SC", xw_privateth;
}
.wrtext :nth-child(1){
  color:var(--color-green);
}
.practice_input{
  justify-self: center;
}
.lastinput{
  display: inline-block;
  font-size: 4rem;
  width: 4rem;
}
.split{
  display: inline-block;
  font-size: 4rem;
  width: 16rem;
  font-family: "更纱黑体 SC", xw_privateth;
}
.practice_input_box{
  font-size: 4rem;
  margin-top: 0px;
  justify-self: center;
  background-color: #202020;
  border-color: #282828;
  border-radius: 10px;
  padding-left: 1px;
  padding-right: 1px;
  margin-right: 0px;
  border-width: 1px;
  border-style: solid;
  padding-left: 10px;
  color: white;
  width: 6rem;
}
.practice_input_box:focus-visible{
  background:none;  	
  outline:none;
  border:none;
  border-width: 1px;
  border-style: solid;
  border-color: #282828;
  background-color: #202020;
}
.practice_input_box:focus{
  border-width: 1px;
  border-style: solid;
  border-color: #282828;
  background-color: #202020;
}


/* radio */
.practice_type{
  font-size:2rem;
  display:flex;
  align-items: center;
  justify-content: center;
}
.practice_type input[type="radio"] {
    display: none;
}
.practice_type span {
    padding: 0 12px;
    display: inline-block;
    background: #181818;
    border-radius: 4px;
    line-height: 28px;
    text-align: center;
    color: #9f9f9f;
    cursor: pointer;
}
.practice_type input:checked+span {
    background: #181818;
    border-color: #5D8ED8;
    color: var(--color-green);
}
.toggle{
  margin: 0;
  padding: 0;
  border: none;
  outline: none;
  text-align: center;
  background-color: #181818;
  color: var(--color-green);
}
.toggle_off{
  color: #a1a1a1;
}
</style>