<template>
  <div>
    <header class="header">
        <div class="back iconfont">&#xe62a;</div>
        <div class="search"></div>
        <div class="city">城市</div>
    </header>
    <swiper ref="mySwiper" :options="swiperOptions">
        <swiper-slide v-for="item in swiperInfo" :key="item.id">
            <div class="swiper-img-con">
                <img class="swiper-img" :src="item.imgUrl"/>
            </div>
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
    </swiper>

    <swiper :options="{}">
        <swiper-slide v-for="(pageInfo,index) in pages" :key="index">
          <div v-for="item in pageInfo" :key="item.id" class="icon-item">
            <div class="icon-img-con">
                <img class="icon-img" :src="item.imgUrl"/>
            </div>
          </div>
        </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data () {
    return {
      swiperInfo: [],
      iconInfo: [],
      swiperOptions: {
        autoplay: 1000,
        direction: 'horizontal',
        pagination: '.swiper-pagination',
        loop: true
      }
    }
  },
  created () {
    this.getIndexData()
  },
  methods: {
    getIndexData () {
      this.$http.get('/static/index.json')
        .then(this.handleGetDataSucc.bind(this))
    },
    handleGetDataSucc (res) {
      const body = res.body
      if (body && body.data && body.data.swiper) {
        this.swiperInfo = body.data.swiper
        this.iconInfo = body.data.icons
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconInfo.forEach((value, index) => {
        let page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(value)
      })
      return pages
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .header {
        display: flex;
        background: #05bad5;
        color: #ffffff;
    }
    .back {
        width: 32px;
        line-height: 43px;
        text-align: center;
    }
    .search {
        flex: 1;
        margin: 7px 9px;
        background: #ffffff;
        border-radius: 5px;
    }
    .city {
        width: 57px;
        line-height: 43px;
        text-align: center;
    }
    .swiper-img-con {
        overflow: hidden;
        width: 100%;
        height: 0;
        padding-bottom: 42.2%;
    }
    .swiper-img {
        width: 100%;
    }
    .icon-item {
        box-sizing: border-box;
        float: left;
        width: 25%;
        padding: .8rem;
    }
    .icon-img-con {
        width: 100%;
        height: 0;
        padding-bottom: 100%;
    }
    .icon-img {
        width: 100%;
    }
</style>
