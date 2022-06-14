<template>
  <div class="info">
    <div class="title">测试截断</div>
    <v-clamp autocapitalize ellipis="'...'" :max-lines="3" :expanded="expanded" class="item">
      这是测试这是测试这是这是测试这是测试这是测试这是测试这是测试这是测试这是测试这是测试测试这是测试这是测试这是测试这是测试这是测试这是测试
    </v-clamp>
    <button @click="toggle()">{{ expanded?'收起':'展开' }}</button>
  </div>
</template>

<script>
import VClamp from 'vue-clamp'
export default {
  name: 'HomeInfo',
  components: {
    VClamp
  },
  data () {
    return {
      expanded: false
    }
  },
  methods: {
    toggle () {
      this.expanded = !this.expanded
    }
  }
}
</script>

<style scoped>
.info{
  width: 100%;
  margin: 0.2rem 0;
}
.item{
  padding: .2rem .1rem;
}
</style>
