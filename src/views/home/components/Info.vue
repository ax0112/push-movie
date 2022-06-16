<template>
  <div class="info">
    <div class="title">{{ this.title }}</div>
    <v-clamp
      ellipis="'...'"
      :max-lines="3"
      :expanded="expanded"
      class="item"
    >
      {{this.content}}
    </v-clamp>
    <button class="ex-btn" @click="toggle()">{{ expanded?'收起':'展开' }}</button>
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
  props: {
    title: String,
    content: String
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
.title{
 font-size: .22rem;
}
.item{
  margin: .2rem .1rem 0 .1rem;
  font-size: .16rem;
  color: #777;
  line-height: .22rem;
}
.ex-btn{
  width: .75rem;
  height: .20rem;
  line-height: .20rem;
  border-radius: 0.2rem;
  background: #25a4bb;
  color: #fff;
  font-size: .16rem;
}
</style>
