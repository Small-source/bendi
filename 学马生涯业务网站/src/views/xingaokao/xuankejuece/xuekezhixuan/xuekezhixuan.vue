<template>
    <div class="xuankejuece">
        <!-- 面包屑导航 -->
        <div class="inner">
            <ul class="innerNav">
                <li><router-link to="/xuekezhixuan/university">大学专业选科要求</router-link></li>
                <li><router-link to="/xuekezhixuan/subject">选科组合可报专业</router-link></li>
            </ul>
            <div class="innerContent">
                <router-view></router-view>
            </div>
        </div>
    </div>
</template>
<style type="text/css" lang='less' scoped>
.xuankejuece {
    background-color: #fff;
    // padding-bottom: 30px;
    min-height: 660px;
    position: relative;
    overflow: hidden;
    .inner {
        width: 1200px;
        margin:30px auto 0;
    }
    // 院校展示
    .yuxiaoBox {
        position: absolute;
        right: -200px;
        top: 0px;
        width: 200px;
        height: 300px;
        background-color: #fff;
        border: 1px solid #dedede;
        border-radius: 3px;
        color: #333;
        font-size: 14px;
        overflow: auto;
        .titlesss {
            text-align: center;
            color: #333;
            font-size: 16px;
            line-height: 40px;
            border-bottom: 1px solid #dedede;
        }
        p {
            font-size: 14px;
            border: 1px dashed #dedede;
            padding-left: 20px;
        }
    }
    // 面包屑导航
    .mianbaoxie {
            margin: 0 auto;
            height: 34px;
            font-size: 12px;
            line-height: 34px;
            color: #666;
            position: relative;
            background-color: #fff;
            margin-bottom: 20px;
            .no1 {
                padding-left: 27px;
                cursor: pointer;
                background: url(/imgs/nav/hourse.png) no-repeat 0px center;
                &:hover {
                    color: #2d90f8;
                }
            }
            .no2 {
                padding-left: 10px;
                cursor: pointer;
                &:hover {
                    color: #2d90f8;
                }
            }
            .no3 {
                padding-left: 10px;
                color: #2d90f8;
            }
            .goBack {
                position: absolute;
                width: 60px;
                height: 30px;
                line-height: 30px;
                background-color: #2d90f8;
                color: #fff;
                right: 0;
                top: 15px;
                border-radius: 2px;
                text-align: center;
                cursor: pointer;
            }
    }
    .subject_direct {
        padding: 0px 20px;
        background-color: #fff;
        .mian_title {
            line-height: 54px;
            font-size: 15px;
            color: #333;
            font-weight: 500;
        }

        .small_title {
            font-size: 14px;
            height: 38px;
            padding: 0px 20px;
            line-height: 38px;
            border: 1px solid #e5e5e5;
            .shezhi {
               margin-right: 10px;
               color: #333;
            }
            .tixing {
                font-size: 12px;
                color: #d83838;
                line-height: 38px;
            }
        }
        .chaxun {
            padding: 11px 20px;
            min-height: 26px;
            border: 1px solid #e5e5e5;
            border-top: 0px solid #e5e5e5;
            background-color: #f9f9f9;
            margin-bottom: 9px;
            .title {
                float: left;
                margin-right: 10px;
            }
            .chaxun2 {
                .top {
                    height: 28px;
                    margin-bottom: 20px;
                }
                .bottom {
                    height: 28px;
                }
            }
        }
        .seleted_title {
            line-height: 45px;
            font-size: 15px;
            color: #333;
        }
        .seleted {
            margin-bottom: 20px;
        }
    }
}
</style>
<script>
import Loading from '../../../.././components/Loading.vue'
export default {
    components: { Loading },
    props: {
        className: {
          type: String,
          default: 'yourClassName'
        },
        id: {
          type: String,
          default: 'yourID'
        },
        width: {
          // type: String,
          default: '1160px'
        },
        height: {
          // type: String,
          default: '500px'
        }
    },
    data() {
        return {
            provance: window.localStorage.getItem('cityNow'),
            chart: null,
        }
    },
    mounted() {
        // this.$router.push('/xuekezhixuan/university')
        $('.innerNav>li').eq(0).find('a').css({background:'#2D8FFC',color:'#F7F5F6'});
        /university/.test(window.location.hash)&&this.activeNav(0);
        /subject/.test(window.location.hash)&&this.activeNav(1);
    },
    watch:{
        $route:{
            handler: function(val, oldVal){
                /university/.test(window.location.hash)&&this.activeNav(0);
                /subject/.test(window.location.hash)&&this.activeNav(1);
            }
        }
    },
    beforeDestroy() {
    },
    methods: {
        //导航激活状态
        activeNav(num){
            $('.innerNav>li>a').css({background:'',color:''})
            $('.innerNav>li').eq(num).find('a').css({background:'#2D8FFC',color:'#F7F5F6'})
        }
    },
    created() {

    }
}
</script>
<style lang="less">
    .innerNav{
        width: 480px;
        display: flex;
        justify-content: space-between;
        margin: 0 auto;
    }
    .innerNav>li{
        width: 220px;
        height: 40px;

    }
    .innerNav>li>a{
        display: block;
        width: 100%;
        height: 100%;
        border-radius: 5px;
        background: #E3E6EB;
        text-align: center;
        line-height: 40px;
        font-size: 16px;
        letter-spacing: 0.1em;
        color:#6D767F;
        font-family: "Microsoft Yahei", Adobe Heiti Std, Arial, sans-serif;
    }
</style>
