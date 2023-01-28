<!-- 整个键盘布局 -->
<script>
import Keyboard from '../components/keyboard/Keyboard.vue'
import { keysStore } from '../stores/keys'

// const keyboard = require('./src/config/keyborad.config');
// import { keyboard } from './config/keyborad.config'

// console.log(keyboard)

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
      keys:keysStore()
    }
  },
  methods:{
    //获取字根或汉字并打乱顺序
    getrandomroots:function(){
      this.croots = this.shuffle(this.keys[this.practice_type])
    },
    inputcheck:function(){
      // console.log(this.keys.wk[this.croots[0]])
      // 判断是否输入正确 当前输入是否等于字根对应的按键
      if(this.currentinput.toUpperCase() == this.keys.wk[this.croots[0]]){
        this.croots.shift()//移除数组第一个元素
        this.highlight()
      }
      this.lastinput = this.currentinput.toUpperCase()
      this.currentinput = ''
    },
    highlight:function(){
      //恢复之前的高亮
      this.keys.lhk.forEach(lhke => {
        this.keys.hk[lhke] = false
      });
      this.keys.lhw.forEach(lhwe => {
        this.keys.hw[lhwe] = false
      });
      //更新样式
      this.keys.hk[this.keys.wk[this.croots[0]]] = true
      this.keys.hw[this.croots[0]] = true
      this.keys.lhk = [this.keys.wk[this.croots[0]]]
      this.keys.lhw = [this.croots[0]]
    },
    change_practice_type:function(){
      this.getrandomroots()
    },
    //乱序数组,洗牌算法
    shuffle:function (arr) {
      let len = arr.length;
      while (len) {
        let randomIndex = Math.floor(Math.random() * len--);
        [arr[randomIndex], arr[len]] = [arr[len], arr[randomIndex]];
      }
      return arr;
    },
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
      <!-- <label for="character">
        <input type="radio" id="character" value="character" v-model="practice_type" @change="change_practice_type" />
        <span>常用字练习</span>
      </label> -->
    </div>
    <div class="wrtext">
      <span v-for="r in this.croots">{{ r }}</span>
    </div>
    <div class="practice_input">
      <div>
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
</style>