<template>
  <div id="test"
    @click="setTarget"
    @mouseenter.capture="setTarget">
    <tool-tip class="custom-tip"
      title="风霜断面"
      :content="content"
      :content-component="contentComponent"
      :content-props="contentData"
      :target="target"
      @transend="target = null">
    </tool-tip>
    <div class="box"
      v-for="index in indexs"
      :style="index">
    </div>
    <div class="arrows"></div>
  </div>
</template>

<script>
import ToolTip from '../src/index.vue'
import Content from './content.vue'

const VW = window.innerWidth || document.documentElement.clientWidth
const VH = window.innerHeight || document.documentElement.clientHeight
function getPosition () {
  return {
    width: (Math.random() * 50 + 50) + 'px',
    height: (Math.random() * 50 + 50) + 'px',
    left: Math.random() * VW + 'px',
    top: Math.random() * VH + 'px'
  }
}
export default {
  data () {
    // this.contentComponent = Content
    this.indexs = [1,2,3,4,5,6,7,8,9].map(it => {
      return getPosition()
    })
    return {
      content: '我本跋涉千艰万险冻地炎群曦盏换星芒\n却只见木纹次第撰写这绮丽炎凉\n抑或用尽这一生颠沛跌宕 刻画心字形状\n最终燃尽那刻定明亮似个彼方\n又有绝美幻象邀我共享这鸩酿\n用曾时构建过简易乌托邦 换刻庭暖花香\n便算风中耳语也渐变温热悠扬\n当极夜降至旖旎这刹风光 或建架草收场\n谁难得凭真实感想领意念疏狂\n我仍可笑容天真不动声响 舐温血以弥伤\n凛冽凌乱尽头或有休憩眠月港',
      contentData: {
        name: 'to',
        value: 'moon'
      },
      target: null
    }
  },

  methods: {
    setTarget ({ target }) {
      if (target.classList.contains('box')) {
        this.target = target
      }
    },

    contentComponent (h) {
      return h('button', '鸩酿')
    }
  },

  components: { ToolTip }
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html, body {
  height: 100%;
  width: 100%;
}

.custom-tip {
  top: 200px;
  left: 300px;
}

.box {
  position: absolute;
  width: 100px;
  height: 100px;
  border: 1px solid #ccc;
}
</style>
