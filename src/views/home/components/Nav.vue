<template>
  <div class="nav">
    <div
      :id="`div${item.id}`"
      v-for="item in NavList"
      :key="item.id"
      class="nav-item"
      @click="handleNavItemClick(item.id)"
    >
      {{ item.text }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeNav',
  mounted () {
    document.getElementById('div1').classList.add('active')
  },
  data () {
    return {
      NavList: [
        {
          id: '1',
          text: '剧情简介'
        },
        {
          id: '2',
          text: '上影推荐'
        },
        {
          id: '3',
          text: '影评讨论'
        }]
    }
  },
  methods: {
    handleNavItemClick (id) {
      this.$emit('change', id)
    }
  }
}
</script>

<style scoped>
.nav {
  position: sticky;
  top: 0;
  width: 100%;
  box-sizing: border-box;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;

}
.nav-item{
  flex: 1;
  border: 1px solid #ccc;
  text-align: center;
  background: #fff;
  font-size: 0.16rem;
  padding: .05rem .15rem ;
}

</style>
