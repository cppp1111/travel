<template>
    <div class="header">
        <div class="header-left">
            <div class="iconfont back-icon">&#xe624;</div>
        </div>
        <div class="header-input">
            <span class="iconfont">&#xe632;</span>
            输入城市/景点/游玩主题
        </div>
        <router-link to='/city'>
            <div class="header-right">
                {{this.city}}
                <span class="iconfont arrow-icon">&#xe62b;</span>
            </div>
        </router-link>
    </div>
</template>
<script>
import {mapGetters, mapState} from 'vuex'

export default{
    name:'HomeHeader',
    computed:{
        // mapState的作用是指vuex里的数据映射到我这个组件的computed计算属性的组件里
        // 映射的是这个公有属性city映射到这个名字叫做city的计算属性之中
        ...mapState(['city']),
        // ...mapGetters(['doubleCity'])
    }
}
</script>
<style scoped lang="stylus">
// @代表目录src，在css中想要引入其他的css，需要加 ~ 
@import '~styles/varibles.styl'
    .header
        display:flex
        line-height: $headerHeight
        background: $bgColor
        color: #fff
        .header-left
            width: .64rem
            float:left
            .back-icon
                text-align: center
                font-size: .4rem
        .header-input
            flex: 1
            height:.64rem
            line-height: .64rem
            padding-left :.2rem
            margin-top:.12rem
            margin-left :.2rem
            background:#fff
            border-radius :.1rem
            color :#ccc
        .header-right
            min-width:1.04rem
            padding 0 .1rem
            float:right
            text-align center
            color: #fff
            .arrow-icon
                margin-left: -.04rem 
                font-size:.24rem
</style>