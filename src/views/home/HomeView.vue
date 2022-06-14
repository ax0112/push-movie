<template>
  <div>
    <home-list-scroll :position="position"></home-list-scroll>
    <div class="nav">
      <div id="div1" class="active" @click="position('list1')">div1</div>
      <div id="div2" @click="position('list2')">div2</div>
      <div id="div3" @click="position('list3')">div3</div>
    </div>
    <home-info></home-info>
    <div id="list1" class="list1" ref="scroll1"></div>
    <div id="list2" class="list2" ref="scroll2"></div>
    <div id="list3" class="list3" ref="scroll3"></div>
  </div>
</template>

<script>
import HomeInfo from '@/views/home/components/Info'
import HomeListScroll from '@/views/home/components/ListScroll'
export default {
  name: 'HomeView',
  components: { HomeListScroll, HomeInfo },
  mounted () {
    window.addEventListener('scroll', this.handleScrollx, true)
  },
  methods: {
    position (key) {
      console.log(key)
      const PageId = document.querySelector('#' + key)
      const Position = PageId.offsetTop - 50
      window.scrollTo({
        top: Position,
        behavior: 'smooth'
      })
    },
    handleScrollx () {
      const list1 = this.$refs.scroll1.getBoundingClientRect().top
      const list2 = this.$refs.scroll2.getBoundingClientRect().top
      const list3 = this.$refs.scroll3.getBoundingClientRect().top
      if (list1 - 100 < 0 && list2 - 100 > 0) {
        document.getElementById('div1').classList.add('active')
        document.getElementById('div2').classList.remove('active')
        document.getElementById('div3').classList.remove('active')
      }
      if (list2 - 100 < 0 && list3 - 100 > 0) {
        document.getElementById('div2').classList.add('active')
        document.getElementById('div1').classList.remove('active')
        document.getElementById('div3').classList.remove('active')
      }
      if (list3 - 100 < 0) {
        document.getElementById('div3').classList.add('active')
        document.getElementById('div1').classList.remove('active')
        document.getElementById('div2').classList.remove('active')
      }
      // const height = list1 - 50
      // if (height < 0) { console.log(list1) }
    }
  }
}
</script>

<style scoped >
.nav {
  position: sticky;
  top: 0;
  width: 100%;
  box-sizing: border-box;
  padding: 0 0.1rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;

}
.nav div{
  flex: 1;
  border: 1px solid #ccc;
  text-align: center;
  background: #fff;
}
.active{
  color: orange;
}
.list1{
  width: 100%;
  height: 600px;
  background: #25a4bb;
}
.list2{
  width: 100%;
  height: 700px;
  background: darkgoldenrod;
}
.list3{
  width: 100%;
  height: 800px;
  background: olive;
}
</style>
