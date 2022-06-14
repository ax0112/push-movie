<template>
<div class="list-scroll">
  <div class="title">这是一个横向移动的盒子</div>
  <div class="wrapper-box" ref="wrapper">
    <div ref="wrapperChild" class="long-box">
      <div class="item" v-for="item of swiper" :key="item.id">
        <div class="item-img" @click="Fposition">
        <img class="item-img-content" :src="item.imgUrl" alt="">
        </div>
          <div class="desc1">{{item.desc1}}</div>
          <div class="desc2">{{ item.desc2}}</div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'HomeListScroll',
  props: {
    position: {
      type: Function,
      default: null
    }
  },
  data () {
    return {
      swiper: [
        {
          id: '01',
          imgUrl: require('../../../assets/image/IMG_2215.png'),
          desc1: '这是评论',
          desc2: '评论'
        },
        {
          id: '02',
          imgUrl: require('../../../assets/image/IMG_2215.png'),
          desc1: '这是评论',
          desc2: '评论'
        },
        {
          id: '03',
          imgUrl: require('../../../assets/image/IMG_2215.png'),
          desc1: '这是评论',
          desc2: '评论'
        },
        {
          id: '04',
          imgUrl: require('../../../assets/image/IMG_2215.png'),
          desc1: '这是评论',
          desc2: '评论'
        },
        {
          id: '05',
          imgUrl: require('../../../assets/image/IMG_2215.png'),
          desc1: '这是评论',
          desc2: '评论'
        }
      ]
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
      let initHeight = 0
      initHeight = rampageList[0].clientHeight
      // 遍历标签
      for (let i = 0; i < rampageList.length; i++) {
        const item = rampageList[i]
        // 将每一个标签宽度相加
        initWidth += item.clientWidth
      }
      // 设置可滚动的宽度
      this.$refs.wrapperChild.style.width = `${initWidth}px`
      this.$refs.wrapperChild.style.height = `${initHeight}px`
    },
    slide_x () {
      this.$nextTick(() => { // this.$nextTick 是一个异步函数，为了确保 DOM 已经渲染完毕
        this._calculateWidth() // 计算宽度
        this._initScroll()
      })
    },
    Fposition () {
      this.position('list2')
    }
  }
}
</script>

<style scoped>
.list-scroll{
  margin: 0.2rem 0;
}
.title{
  font-size: .24rem;
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
  height: 1.52rem;
  padding: 0 .05rem;
}
.item-img{
  width: 100%;
  height: 1rem;
  overflow: hidden;
}
.item-img-content{
  width: 100%;
}
.desc1{
  line-height: .26rem;
  font-size: .16rem;
}
.desc2{
  line-height: .13rem;
  font-size: .08rem;
}
</style>
