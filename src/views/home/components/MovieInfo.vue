<template>
  <div class="info">
    <div class="info-img">
      <img :src="imgUrl" alt="">
    </div>
    <div class="info-text">
      <v-clamp class="info-text-title" :autoresize="true" ellipis="'...'" :max-lines="2" :expanded="false">
        {{ title }}
      </v-clamp>
      <p class="info-text-classification">{{ classification }}</p>
      <div class="info-text-desc">
        <p>{{'上影评分: '+ desc.SRemark}}</p>
        <p>{{'豆瓣评分: '+ desc.DRemark }}</p>
        <p>{{'观影渠道: '+ desc.source}}<a>前往</a></p>
      </div>
    </div>
  </div>
</template>

<script>
import VClamp from 'vue-clamp'
export default {
  name: 'MovieInfo',
  components: {
    VClamp
  },
  props: {
    title: String,
    imgUrl: String,
    classification: String,
    desc: {
      type: Object,
      default () {
        return {
          SRemark: String,
          DRemark: String,
          source: String
        }
      }
    }
  },
  data () {
    return {
      autoresize: true
    }
  }
}
</script>

<style scoped>
.info{
  width: 100%;
  display: flex;
  flex-direction: row;
  padding: 0.2rem 0.1rem;
  box-sizing: border-box;
}
.info-img{
  height: 1.52rem;
  overflow: hidden;
}
.info-img img{
  height: 100%;
}
.info-text{
  position: relative;
  flex: 1;
  width: 2.18rem;
  padding-left:.2rem;
}
.info-text-title{
  font-size: .24rem;
  line-height: .26rem;
}
.info-text-classification{
  font-size: .16rem;
  color: #777;
  margin-top: .10rem;
}
.info-text-desc{
  position: absolute;
  bottom: 0;
  font-size: .16rem;
  color: #777;
}
.info-text-desc p{
  line-height: .20rem;
}
</style>
