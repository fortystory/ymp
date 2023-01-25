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
      wroot:{
        "革":"Q_g_0",
        "臣":"Q_g_1",
        "因":"Q_g_2",
        "旦":"Q_g_3",
        "今":"Q_g_4",
        "令":"Q_g_5",
        "丘":"Q_g_6",
        "斤":"Q_g_7",
        "六":"Q_g_8",
        "米":"Q_g_9",
        "民":"Q_g_10",
        "叚":"Q_g_11",
        "":"Q_p_0",
        "朿":"Q_p_1",
        "":"Q_p_2",
        "𢦏":"Q_p_3",
        "亼":"Q_p_4",
        "冖":"Q_p_5",
        "㐫":"Q_p_6",
        "㡀":"Q_p_7",
        "去":"W_g_0",
        "求":"W_g_1",
        "万":"W_g_2",
        "日":"W_g_3",
        "曰":"W_g_4",
        "我":"W_g_5",
        "毛":"W_g_6",
        "川":"W_g_7",
        "象":"W_g_8",
        "曾":"W_g_9",
        "力":"W_g_10",
        "乃":"W_g_11",
        "⺀":"W_p_0",
        "冫":"W_p_1",
        "丷":"W_p_2",
        "":"W_p_3",
        "":"W_p_4",
        "":"W_p_5",
        "":"W_p_6",
        "":"W_p_7",
        "彡":"W_p_8",
        "":"W_p_9",
        "巛":"W_p_10",
        "":"W_p_11",
        "卩":"W_p_12",
        "⼀":"E_s_0",
        "辶":"R_p_0",
        "廴":"R_p_1",
        "⼂":"R_s_0",
        "才":"T_g_0",
        "木":"T_g_1",
        "西":"T_g_2",
        "酉":"T_g_3",
        "此":"T_g_4",
        "占":"T_g_5",
        "用":"T_g_6",
        "鼠":"T_g_7",
        "久":"T_g_8",
        "臼":"T_g_9",
        "户":"T_g_10",
        "加":"T_g_11",
        "甬":"T_g_12",
        "乛":"T_p_0",
        "㇕":"T_p_1",
        "㇆":"T_p_2",
        "":"T_p_3",
        "㇉":"T_p_4",
        "㇡":"T_p_5",
        "":"T_p_6",
        "":"T_p_7",
        "":"T_p_8",
        "":"T_p_9",
        "而":"Y_g_0",
        "二":"Y_g_1",
        "莫":"Y_g_2",
        "辰":"Y_g_3",
        "车":"Y_g_4",
        "井":"Y_g_5",
        "耳":"Y_g_6",
        "堇":"Y_g_7",
        "山":"Y_g_8",
        "巾":"Y_g_9",
        "化":"Y_g_10",
        "缶":"Y_g_11",
        "瓜":"Y_g_12",
        "爪":"Y_g_13",
        "麻":"Y_g_14",
        "兼":"Y_g_15",
        "习":"Y_g_16",
        "羽":"Y_g_17",
        "":"Y_p_0",
        "":"Y_p_1",
        "爫":"Y_p_2",
        "":"Y_p_3",
        "癶":"Y_p_4",
        "":"Y_p_5",
        "":"Y_p_6",
        "阝":"Y_p_7",
        "":"Y_p_8",
        "":"Y_p_9",
        "ㄋ":"U_s_0",
        "⼁":"I_s_0",
        "⼃":"O_s_0",
        "三":"P_g_0",
        "十":"P_g_1",
        "犬":"P_g_2",
        "尧":"P_g_3",
        "共":"P_g_4",
        "雨":"P_g_5",
        "食":"P_g_6",
        "舟":"P_g_7",
        "卯":"P_g_8",
        "定":"P_g_9",
        "次":"P_g_10",
        "火":"P_g_11",
        "亦":"P_g_12",
        "乙":"P_g_13",
        "幺":"P_g_14",
        "":"P_p_0",
        "龷":"P_p_1",
        "":"P_p_2",
        "":"P_p_3",
        "犭":"P_p_4",
        "饣":"P_p_5",
        "":"P_p_6",
        "":"P_p_7",
        "":"P_p_8",
        "":"P_p_9",
        "":"P_p_10",
        "":"P_p_11",
        "乚":"P_p_12",
        "于":"A_g_0",
        "亍":"A_g_1",
        "丁":"A_g_2",
        "厂":"A_g_3",
        "牙":"A_g_4",
        "由":"A_g_5",
        "曲":"A_g_6",
        "甲":"A_g_7",
        "几":"A_g_8",
        "仑":"A_g_9",
        "尔":"A_g_10",
        "欠":"A_g_11",
        "前":"A_g_12",
        "广":"A_g_13",
        "马":"A_g_14",
        "丑":"A_g_15",
        "":"A_p_0",
        "":"A_p_1",
        "":"A_p_2",
        "":"A_p_3",
        "":"A_p_4",
        "":"A_p_5",
        "王":"S_g_0",
        "是":"S_g_1",
        "亚":"S_g_2",
        "示":"S_g_3",
        "呆":"S_g_4",
        "分":"S_g_5",
        "壬":"S_g_6",
        "鬼":"S_g_7",
        "及":"S_g_8",
        "言":"S_g_9",
        "子":"S_g_10",
        "孑":"S_g_11",
        "聿":"S_g_12",
        "刀":"S_g_13",
        "凵":"S_g_14",
        "":"S_p_0",
        "冂":"S_p_1",
        "":"S_p_2",
        "讠":"S_p_3",
        "屰":"S_p_4",
        "":"S_p_5",
        "石":"D_g_0",
        "未":"D_g_1",
        "末":"D_g_2",
        "耒":"D_g_3",
        "甘":"D_g_4",
        "廿":"D_g_5",
        "执":"D_g_6",
        "贝":"D_g_7",
        "虍":"D_g_8",
        "人":"D_g_9",
        "入":"D_g_10",
        "白":"D_g_11",
        "鱼":"D_g_12",
        "卑":"D_g_13",
        "豸":"D_g_14",
        "殳":"D_g_15",
        "酋":"D_g_16",
        "穴":"D_g_17",
        "也":"D_g_18",
        "糸":"D_g_19",
        "":"D_p_0",
        "":"D_p_1",
        "":"D_p_2",
        "":"D_p_3",
        "":"D_p_4",
        "":"D_p_5",
        "":"D_p_6",
        "天":"F_g_0",
        "者":"F_g_1",
        "甫":"F_g_2",
        "见":"F_g_3",
        "从":"F_g_4",
        "夭":"F_g_5",
        "彳":"F_g_6",
        "八":"F_g_7",
        "鸟":"F_g_8",
        "门":"F_g_9",
        "又":"F_g_10",
        "双":"F_g_11",
        "艹":"F_p_0",
        "":"F_p_1",
        "":"F_p_2",
        "":"F_p_3",
        "":"F_p_4",
        "":"F_p_5",
        "可":"G_g_0",
        "其":"G_g_1",
        "至":"G_g_2",
        "里":"G_g_3",
        "田":"G_g_4",
        "畀":"G_g_5",
        "生":"G_g_6",
        "先":"G_g_7",
        "段":"G_g_8",
        "九":"G_g_9",
        "已":"G_g_10",
        "己":"G_g_11",
        "巴":"G_g_12",
        "巳":"G_g_13",
        "扌":"G_p_0",
        "":"G_p_1",
        "":"G_p_2",
        "":"G_p_3",
        "不":"H_g_0",
        "青":"H_g_1",
        "直":"H_g_2",
        "面":"H_g_3",
        "平":"H_g_4",
        "圭":"H_g_5",
        "豆":"H_g_6",
        "豕":"H_g_7",
        "止":"H_g_8",
        "齿":"H_g_9",
        "凹":"H_g_10",
        "凸":"H_g_11",
        "光":"H_g_12",
        "月":"H_g_13",
        "立":"H_g_14",
        "角":"H_g_15",
        "立":"H_g_16",
        "单":"H_g_17",
        "忄":"H_p_0",
        "礻":"H_p_1",
        "衤":"H_p_2",
        "":"H_p_3",
        "":"H_p_4",
        "":"H_p_5",
        "":"H_p_6",
        "":"H_p_7",
        "":"H_p_8",
        "":"H_p_9",
        "厃":"H_p_10",
        "":"H_p_11",
        "一":"J_g_0",
        "夫":"J_g_1",
        "五":"J_g_2",
        "丌":"J_g_3",
        "瓦":"J_g_4",
        "韦":"J_g_5",
        "寸":"J_g_6",
        "业":"J_g_7",
        "自":"J_g_8",
        "告":"J_g_9",
        "勿":"J_g_10",
        "衣":"J_g_11",
        "半":"J_g_12",
        "":"J_p_0",
        "":"J_p_1",
        "亻":"J_p_2",
        "":"J_p_3",
        "":"J_p_4",
        "":"J_p_5",
        "㇐":"J_p_6",
        "㇑":"J_p_7",
        "㇔":"J_p_8",
        "㇓":"J_p_9",
        "大":"K_g_0",
        "正":"K_g_1",
        "戊":"K_g_2",
        "弋":"K_g_3",
        "戈":"K_g_4",
        "戋":"K_g_5",
        "敖":"K_g_6",
        "口":"K_g_7",
        "囗":"K_g_8",
        "片":"K_g_9",
        "之":"K_g_10",
        "主":"K_g_11",
        "羊":"K_g_12",
        "尺":"K_g_13",
        "爿":"K_p_0",
        "":"K_p_1",
        "":"K_p_2",
        "":"K_p_3",
        "":"K_p_4",
        "":"K_p_5",
        "":"K_p_6",
        "":"K_p_7",
        "下":"L_g_0",
        "元":"L_g_1",
        "工":"L_g_2",
        "龙":"L_g_3",
        "士":"L_g_4",
        "土":"L_g_5",
        "鬲":"L_g_6",
        "上":"L_g_7",
        "卜":"L_g_8",
        "内":"L_g_9",
        "父":"L_g_10",
        "竹":"L_g_11",
        "心":"L_g_12",
        "京":"L_g_13",
        "农":"L_g_14",
        "𥫗":"L_p_0",
        "𡗗":"L_p_1",
        "龹":"L_p_2",
        "疒":"L_p_3",
        "⽱":"L_p_4",
        "":"L_p_5",
        "":"L_p_6",
        "":"L_p_7",
        "":"L_p_8",
        "":"L_p_9",
        "":"L_p_10",
        "":"L_p_11",
        "束":"Z_g_0",
        "非":"Z_g_1",
        "北":"Z_g_2",
        "身":"Z_g_3",
        "垂":"Z_g_4",
        "各":"Z_g_5",
        "乍":"Z_g_6",
        "皮":"Z_g_7",
        "尸":"Z_g_8",
        "":"Z_p_0",
        "":"Z_p_1",
        "":"Z_p_2",
        "丬":"Z_p_3",
        "丰":"X_g_0",
        "尢":"X_g_1",
        "回":"X_g_2",
        "黑":"X_g_3",
        "儿":"X_g_4",
        "刍":"X_g_5",
        "弟":"X_g_6",
        "亡":"X_g_7",
        "发":"X_g_8",
        "弓":"X_g_9",
        "":"X_p_0",
        "":"X_p_1",
        "":"X_p_2",
        "":"X_p_3",
        "纟":"X_p_4",
        "":"X_p_5",
        "𠂔":"X_p_6",
        "":"X_p_7",
        "丽":"C_g_0",
        "赤":"C_g_1",
        "小":"C_g_2",
        "四":"C_g_3",
        "皿":"C_g_4",
        "公":"C_g_5",
        "牛":"C_g_6",
        "合":"C_g_7",
        "禾":"C_g_8",
        "了":"C_g_9",
        "尹":"C_g_10",
        "奴":"C_g_11",
        "彐":"C_p_0",
        "罒":"C_p_1",
        "":"C_p_2",
        "":"C_p_3",
        "":"C_p_4",
        "":"C_p_5",
        "":"C_p_6",
        "":"C_p_7",
        "":"C_p_8",
        "牜":"C_p_9",
        "厶":"C_p_10",
        "":"C_p_11",
        "相":"V_g_0",
        "古":"V_g_1",
        "中":"V_g_2",
        "少":"V_g_3",
        "气":"V_g_4",
        "矢":"V_g_5",
        "金":"V_g_6",
        "母":"V_g_7",
        "毋":"V_g_8",
        "毌":"V_g_9",
        "匚":"V_p_0",
        "コ":"V_p_1",
        "":"V_p_2",
        "":"V_p_3",
        "":"V_p_4",
        "钅":"V_p_5",
        "宀":"V_p_6",
        "更":"B_g_0",
        "髟":"B_g_1",
        "歹":"B_g_2",
        "屯":"B_g_3",
        "目":"B_g_4",
        "且":"B_g_5",
        "虫":"B_g_6",
        "长":"B_g_7",
        "代":"B_g_8",
        "乎":"B_g_9",
        "争":"B_g_10",
        "夕":"B_g_11",
        "以":"B_g_12",
        "辟":"B_g_13",
        "":"B_p_0",
        "":"B_p_1",
        "":"B_p_2",
        "":"B_p_3",
        "":"B_p_4",
        "":"B_p_5",
        "":"B_p_6",
        "":"B_p_7",
        "开":"N_g_0",
        "干":"N_g_1",
        "吉":"N_g_2",
        "页":"N_g_3",
        "七":"N_g_4",
        "廾":"N_g_5",
        "水":"N_g_6",
        "手":"N_g_7",
        "千":"N_g_8",
        "匕":"N_g_9",
        "舌":"N_g_10",
        "文":"N_g_11",
        "义":"N_g_12",
        "辛":"N_g_13",
        "":"N_p_0",
        "":"N_p_1",
        "":"N_p_2",
        "氵":"N_p_3",
        "":"N_p_4",
        "灬":"N_p_5",
        "":"N_p_6",
        "":"N_p_7",
        "":"N_p_8",
        "刂":"N_p_9",
        "":"N_p_10",
        "夂":"N_p_11",
        "":"N_p_12",
        "":"N_p_13",
        "":"N_p_14",
        "":"N_p_15",
        "":"N_p_16",
        "走":"M_g_0",
        "云":"M_g_1",
        "林":"M_g_2",
        "区":"M_g_3",
        "比":"M_g_4",
        "折":"M_g_5",
        "骨":"M_g_6",
        "氏":"M_g_7",
        "隹":"M_g_8",
        "方":"M_g_9",
        "音":"M_g_10",
        "鹿":"M_g_11",
        "女":"M_g_12",
        "疋":"M_p_0",
        "":"M_p_1",
        "龰":"M_p_2",
        "":"M_p_3",
        "":"M_p_4",
      },
      croots:[],
      currentinput:'',
      lastinput:'',
      lastHighlight:'',
      keys:keysStore()
    }
  },
  methods:{
    //获取字根并打乱顺序
    getrandomroots:function(){
      this.croots = Object.keys(this.wroot).sort((a, b) => Math.random() - 0.5);
      // console.log(this.croots);
      this.highlightFirstRoot()
    },
    inputcheck:function(){
      // console.log("inputcheck",this.currentinput,this.lastinput)
      this.lastinput = this.currentinput
      let key = this.currentinput.toUpperCase()
      this.currentinput = ''
      // this.currentinput = this.lastinput
      let croot = this.wroot[this.croots[0]];
      let keyname = croot[0]
      if(key == keyname){
        console.log("OK");
        this.croots.shift();
        this.highlightFirstRoot()
      }
    },
    highlightFirstRoot:function(){
      //还原样式
      if(this.lastHighlight != ''){
        document.querySelector("#"+this.lastHighlight).setAttribute('class','character');
        document.querySelector("#buttonShell_"+this.lastHighlight[0]).setAttribute('class','buttonShell');
      }
      //更新样式
      let id = this.wroot[this.croots[0]];
      document.querySelector("#"+id).setAttribute('class','highlight');
      document.querySelector("#buttonShell_"+id[0]).setAttribute('class','buttonShell highlight_button');
      this.lastHighlight = id;
    },
  },
  mounted(){
    // console.log(Object.keys(this.wroot)); 
    this.getrandomroots();
  }
}
</script>

<template>
  <div class="practice">
    <div class="kboard">
      <Keyboard />
    </div>
    <div class="wrtext">
      <span v-for="r in this.croots">{{ r }}</span>
    </div>
    <div class="practice_input">
      <!-- 配置开关 -->
      <!-- practice_input -->
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
  grid-template-rows: 7fr 3fr 2fr;
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
.practice_input{
  justify-self: center;
}
.lastinput{
  font-size: 4rem;
  margin-right: 50px;
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
.highlight{
  color:#fff;
}
.highlight_button{
  background-color: #303030;
}
</style>