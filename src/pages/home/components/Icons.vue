<template>
    <div class="icons">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(page,index) of pages" :key="index">
                <div class="icon" v-for="item of page" :key="item.id">
                    <div class="icon-img">
                        <img class="icon-imgcontent" :src="item.imgUrl" alt="">
                    </div>
                    <p class="icon-desc">{{item.desc}}</p>
                </div>
            </swiper-slide>
        </swiper>
    </div>
</template>
<script>

export default {
    name:"HomeIcons",
    props:{
        list:Array
    },data(){
        return{
            swiperOption:{
                autoplay:false
            }
        }
    },
    computed : {
        pages () {
            const pages = []
            this.list.forEach((item,index) =>{
                const page = Math.floor(index / 8)
                if(!pages[page]){
                    pages[page]=[]
                }
                pages[page].push(item)
            })
            return pages
        }
    }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
    .icons >>> .swiper-container
        height: 0
        // 这里是指高度是相对于宽度百分百的百分之50
        padding-bottom :50%
        // background :green
    .icons
        margin-top :.1rem
        .icon
            position: relative
            overflow :hidden
            vertical-align :middle
            float :left
            width :25%
            height :0
            padding-bottom :25%
            // background :red
            border: 0
            .icon-img
                // text-align :center
                position :absolute
                top:0
                left:0
                right :0
                bottom:.44rem
                box-sizing :1rem
                padding:.1rem
                // background :blue
                .icon-imgcontent
                    height :100%
                    display :block
                    margin:0 auto
            .icon-desc
                position :absolute
                left:0
                right :0
                bottom:0
                height :.44rem
                line-height :.44rem
                color :$darkTextColor
                text-align :center
                ellipsis()
</style>