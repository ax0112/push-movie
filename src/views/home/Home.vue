<template>
  <div>
    <home-header></home-header>
    <movie-info
      :title="MovieInfo.title"
      :img-url="MovieInfo.imgUrl"
      :classification="MovieInfo.classification"
      :desc="MovieInfo.desc"
    ></movie-info>
    <div class="main-content">
      <home-nav></home-nav>
      <home-info :title="InfoList[0].title" :content="InfoList[0].content"></home-info>
      <home-list-scroll :swiper="swiper" title="演职员" height="75" width="75"></home-list-scroll>
      <home-info :title="InfoList[1].title" :content="InfoList[1].content"></home-info>
      <home-list-scroll :swiper="swiper1" title="上影推剪辑" height="88" width="135"></home-list-scroll>
      <home-list-scroll :swiper="swiper2" title="上影推图" height="88" width="135"></home-list-scroll>
    </div>
  </div>
</template>

<script>
import HomeHeader from '@/views/home/components/Header'
import MovieInfo from '@/views/home/components/MovieInfo'
import HomeNav from '@/views/home/components/Nav'
import HomeInfo from '@/views/home/components/Info'
import HomeListScroll from '@/views/home/components/ListScroll'
export default {
  name: 'HomeView',
  components: { HomeListScroll, HomeInfo, HomeNav, MovieInfo, HomeHeader },
  data () {
    return {
      MovieInfo: {
        title: '为美好的世界献上祝福！红传说 这是测试这是测试这是测试',
        imgUrl: require('../../assets/image/wVrnWi9rUXAH22u6upt6u8eRW5a.jpeg'),
        classification: '90分钟, 动画, 冒险, 喜剧, 奇幻 ',
        desc: {
          SRemark: '未知',
          DRemark: '未知',
          source: 'xxx BT'
        }
      },
      InfoList: [
        {
          title: '剧情简介',
          content: '本应由于交通事故（!?）导致人生轻易闭幕的游戏迷家里蹲·佐藤和真，事出偶然地带着女神·阿库娅转生到了异世界。“在如同RPG游戏一样的异世界，享受憧憬已久的冒险者生活！目标是勇者！”像这样兴奋了还没多久，转生而来的和真就尽是遇到倒霉的事情。 麻烦制造机废柴女神·阿库娅，重度中二病魔法使·惠惠，妄想停不下来的女骑士·达克妮丝，和真与空有高超能力值却无比残念的这3人组队，欠下一屁股债，涉嫌颠覆国家罪而遭到审判，讨伐魔王军干部，偶尔还会死一死…… 这样的某一天，突然跑来的红魔族少女·悠悠的一句爆炸性发言，让和真等人当场石化。“我想要和真先生的孩子！”问明原因，原来惠惠和悠悠的故乡“红魔之里” 目前正濒临灭亡的危机。追在出发前去拯救村落的悠悠后面，和真等人向着红魔之里出发，但——！？向和真小队袭来的最大危机！平凡的冒险者和真度过的异世界生活，未来究竟会怎样！'
        },
        {
          title: '上影推荐',
          content: '本应由于交通事故（!?）导致人生轻易闭幕的游戏迷家里蹲·佐藤和真，事出偶然地带着女神·阿库娅转生到了异世界。“在如同RPG游戏一样的异世界，享受憧憬已久的冒险者生活！目标是勇者！”像这样兴奋了还没多久，转生而来的和真就尽是遇到倒霉的事情。 麻烦制造机废柴女神·阿库娅，重度中二病魔法使·惠惠，妄想停不下来的女骑士·达克妮丝，和真与空有高超能力值却无比残念的这3人组队，欠下一屁股债，涉嫌颠覆国家罪而遭到审判，讨伐魔王军干部，偶尔还会死一死…… 这样的某一天，突然跑来的红魔族少女·悠悠的一句爆炸性发言，让和真等人当场石化。“我想要和真先生的孩子！”问明原因，原来惠惠和悠悠的故乡“红魔之里” 目前正濒临灭亡的危机。追在出发前去拯救村落的悠悠后面，和真等人向着红魔之里出发，但——！？向和真小队袭来的最大危机！平凡的冒险者和真度过的异世界生活，未来究竟会怎样！？'
        }
      ],
      swiper: [
        {
          id: '01',
          imgUrl: require('../../assets/image/IMG_2215.png'),
          desc1: '姓名',
          desc2: '职位'
        },
        {
          id: '02',
          imgUrl: require('../../assets/image/IMG_2216.png'),
          desc1: '姓名',
          desc2: '职位'
        },
        {
          id: '03',
          imgUrl: require('../../assets/image/IMG_2217.png'),
          desc1: '姓名',
          desc2: '职位'
        },
        {
          id: '04',
          imgUrl: require('../../assets/image/IMG_2215.png'),
          desc1: '姓名',
          desc2: '职位'
        },
        {
          id: '05',
          imgUrl: require('../../assets/image/IMG_2216.png'),
          desc1: '姓名',
          desc2: '职位'
        }
      ],
      swiper1: [
        {
          id: '01',
          imgUrl: require('../../assets/image/IMG_2215.png'),
          desc3: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          played: '1000播放'
        },
        {
          id: '02',
          imgUrl: require('../../assets/image/IMG_2216.png'),
          desc3: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          played: '1000播放'
        },
        {
          id: '03',
          imgUrl: require('../../assets/image/IMG_2217.png'),
          desc3: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          played: '1000播放'
        },
        {
          id: '04',
          imgUrl: require('../../assets/image/IMG_2215.png'),
          desc3: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          played: '1000播放'
        },
        {
          id: '05',
          imgUrl: require('../../assets/image/IMG_2216.png'),
          desc3: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试',
          played: '1000播放'
        }
      ],
      swiper2: [
        {
          id: '01',
          imgUrl: require('../../assets/image/IMG_2215.png'),
          desc3: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试'
        },
        {
          id: '02',
          imgUrl: require('../../assets/image/IMG_2216.png'),
          desc3: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试'
        },
        {
          id: '03',
          imgUrl: require('../../assets/image/IMG_2217.png'),
          desc3: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试'
        },
        {
          id: '04',
          imgUrl: require('../../assets/image/IMG_2215.png'),
          desc3: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试'
        },
        {
          id: '05',
          imgUrl: require('../../assets/image/IMG_2216.png'),
          desc3: '测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试测试'
        }
      ]
    }
  }
}
</script>

<style scoped>
.main-content{
  width: 100%;
  padding: 0 .2rem;
  box-sizing: border-box;
}
</style>
