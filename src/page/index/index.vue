<template>
  <div>
    <header class="header">
        <div class="back iconfont">&#xe62a;</div>
        <div class="search"></div>
        <div class="city">城市</div>
    </header>
    <swiper ref="mySwiper" :options="swiperOptions">
        <swiper-slide>
            <div class="swiper-img-con">
                <img class="swiper-img" src="https://dimg04.c-ctrip.com/images/a10e15000000yexmx6853_W_500_0.jpg_.webp"/>
            </div>
        </swiper-slide>
        <swiper-slide>
            <div class="swiper-img-con">
                <img class="swiper-img" src="https://dimg04.c-ctrip.com/images/a10d1c000001cgvba5852_W_500_0.jpg_.webp"/>
            </div>
        </swiper-slide>
        <swiper-slide>
            <div class="swiper-img-con">
                <img class="swiper-img" src="https://dimg04.c-ctrip.com/images/a10k1f000001g288d6790_W_500_0.png_.webp"/>
            </div>
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data () {
    return {
      swiperOptions: {
        autoplay: 1000,
        direction: 'horizontal'
      }
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
        width: 100%;
    }
    .swiper-img {
        width: 100%;
    }
</style>
