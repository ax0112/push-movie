<template>
<div class="list-scroll">
  <div class="title">{{ title }}</div>
  <div class="wrapper-box" ref="wrapper">
    <div ref="wrapperChild" class="long-box">
      <div
        class="item"
        v-for="item of swiper"
        :key="item.id"
        :style="[{'width':width+'px'}]"
      >
        <div
          class="item-img"
          :style="[{'height':height+'px'}]">
          <img
            class="item-img-content"
            :src="item.imgUrl" alt=""
          >
          <span class="item-img-text">{{item.played}}</span>
        </div>
        <div class="item-text">
          <div class="desc">{{item.desc1}}</div>
          <div class="desc">{{ item.desc2}}</div>
          <v-clamp :autoresize="autoresize" :max-lines="2" class="desc">{{item.desc3}}</v-clamp>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import BScroll from 'better-scroll'
import VClamp from 'vue-clamp'
export default {
  name: 'HomeListScroll',
  components: {
    VClamp
  },
  props: {
    title: String,
    swiper: {
      type: Array,
      default () {
        return [{
          id: String,
          imgUrl: String,
          desc1: String,
          desc2: String,
          desc3: String,
          played: String
        }]
      }
    },
    height: String,
    width: String
  },
  data () {
    return {
      autoresize: true
    }
  },
  mounted () {
    this.slide_x()
  },
  methods: {
    // 初始化
    _initScroll () {
      if (!this.scroll) {
        this.scroll = new BScroll(this.$refs.wrapper, { // 实例化BScroll接受两个参数，第一个为父盒子的dom节点
          startX: 0, /// 配置的详细信息请参考better-scroll的官方文档，这里不再赘述
          click: true,
          scrollX: true,
          scrollY: false, // 忽略竖直方向的滚动
          eventPassthrough: 'vertical',
          useTransition: false // 防止快速滑动触发的异常回弹
        })
      } else {
        this.scroll.refresh() // 如果dom结构发生改变调用该方法重新计算来确保滚动效果的正常
      }
    },
    // 计算宽度
    _calculateWidth () {
      // 获取类名为 imgItem 的标签
      const rampageList = this.$refs.wrapperChild.getElementsByClassName(
        'item'
      )
      // 设置一个起始宽度
      let initWidth = 0
      // 遍历标签
      for (let i = 0; i < rampageList.length; i++) {
        const item = rampageList[i]
        // 将每一个标签宽度相加
        initWidth += item.clientWidth
      }
      // 设置可滚动的宽度
      this.$refs.wrapperChild.style.width = `${initWidth}px`
    },
    slide_x () {
      this.$nextTick(() => { // this.$nextTick 是一个异步函数，为了确保 DOM 已经渲染完毕
        this._calculateWidth() // 计算宽度
        this._initScroll()
      })
    }
  }
}
</script>

<style scoped>
.list-scroll{
  margin: 0.2rem 0;
}
.title{
  font-size: .22rem;
}
.wrapper-box{
  overflow: hidden;
  width: 100%;
}
.long-box{
  width: 0;
}
.item{
  float: left;
  width: 1.2rem;
  padding: 0 .05rem;
}
.item-img{
  position: relative;
  width: 100%;
  height: 1rem;
  overflow: hidden;
}
.item-img-content{
  width: 100%;
}
.item-img-text{
  position: absolute;
  width: 100%;
  background: rgba(0, 0, 0, 0.5);
  border-radius: 0.01rem;
  font-size: .12rem;
  color: #fff;
  bottom: 0;
  right: 0;
  text-align: right;
}
.item-text{
  height: .5rem;
  padding: .1rem 0;
}
.desc{
  line-height: .18rem;
  font-size: .16rem;
  color: #777777;
}

</style>
