<template>
    <div class="jihuomajor">
        <div class="tanchuang1" v-show="!isJihuo">
            <div class="title">激活根据专业选科目卡</div>
            <!-- <form action=""> -->
                <p class="neirong">
                    <input type="text" v-model="XuankekaNumber" placeholder="请输入根据专业选科目卡账号" class="Username" >
                </p>
                <!-- <p class="warning">{{warning1}}</p> -->
                <p class="neirong2">
                    <input type="password" v-model="Xuankekapassword" placeholder="请输入根据专业选科目卡密码" class="Password1">
                </p>
                <p class="warning">{{warning4}}</p>
                <button @click="goJihuo">确定</button>
            <!-- </form>     -->
            <div class="close" @click="$emit('go-back')">
                X
            </div>
        </div>
        <div class="tanchuang2" v-show="isJihuo">
            <div class="tubiao"><img src="/imgs/tongyongtanchuang/chenggo ng.png" alt=""></div>
            <div class="title">激活成功</div>
            <p class="tishiyu">点击确定前往选科</p>
            <button class="goback" @click="$router.push('/elective/majorSelectedSubjects/mubiaozhuanye')">确定</button>
        </div>
    </div>
</template>
<style type="text/css" lang='less' scoped>
    .jihuomajor{
        position: fixed;
        left: 0px;
        top: 0px;
        right: 0px;
        bottom: 0px;
        z-index: 100;
        background-color: rgba(51,51,51,.25);
        text-align: center;
        .inner {
            width: 1200px;
            margin: 0 auto;
        }
        .tanchuang1 {
            position: absolute;
            box-sizing: border-box;
            padding: 20px 50px;
            // background-color: #fff;
            left: 50%;
            top: 150px;
            margin-left: -245px;
            width: 490px;
            height: 350px;
            background-color: #fff;
            .Username {
                background: url(/imgs/selfAssessment/touxiang.png) no-repeat 10px center;
            }
            .Password1 {
                background: url(/imgs/selfAssessment/mima.png) no-repeat 10px center;
            }
            .title {
                font-size: 18px;
                color: #2c8ffc;
                line-height: 58px;
                border-bottom: 2px solid #2c8ffc;
                margin-bottom: 30px;
            }
            .neirong {
                height: 50px;
                margin-bottom: 30px;
                input {
                    width: 338px;
                    padding-left: 50px;
                    height: 50px;
                    border: none;
                    border-radius: 3px;
                    border: 1px solid #cfcfcf;
                }
            }
            .neirong2 {
                height: 50px;
                // margin-bottom: 30px;
                input {
                    width: 338px;
                    padding-left: 50px;
                    height: 50px;
                    border: none;
                    border-radius: 3px;
                    border: 1px solid #cfcfcf;
                }
            }
            .warning {
                height: 35px;
                line-height: 35px;
                font-size: 14px;
                color: red;
            }
            button {
                width: 100%;
                height: 50px;
                font-size: 14px;
                color: #fff;
                background-color: #2c8ffc;
                border-radius: 5px;
                border: none;
                cursor: pointer;
            }
            .close {
                width: 36px;
                height: 36px;
                border-radius: 50%;
                z-index: 2;
                // width: 100%;
                // height: 100%;
                color: #fff;
                position: absolute;
                line-height: 36px;
                text-align: center;
                right: -18px;
                top: -18px;
                background-color: #e7e4e4;
                cursor: pointer;
            }
        }
        .tanchuang2 {
            position: absolute;
            box-sizing: border-box;
            padding: 50px 50px 24px 50px;
            // background-color: #fff;
            left: 50%;
            top: 150px;
            margin-left: -245px;
            width: 490px;
            height: 350px;
            background-color: #fff;
            text-align: center;
            .tubiao {
                width: 80px;
                height: 80px;
                border-radius: 50%;
                margin: 0 auto;
                overflow: hidden;
            }
            .title {
                padding-top: 20px;
                line-height: 38px;
                color: #333;
                font-size: 18px;
            }
            .tishiyu {
                line-height: 34px;
                height: 34px;
                font-size: 14px;
                color: #666;
                margin-bottom: 40px;
            }
            .goback {
                width: 100%;
                height: 50px;
                font-size: 14px;
                color: #fff;
                background-color: #2c8ffc;
                border-radius: 5px;
                border: none;
            }
        }

    }
</style>
<script>
    export default {
        props: ['serial_no' ],
        data() {
            return {
                // 选科卡账号
                XuankekaNumber: '',
                // 选科卡密码
                Xuankekapassword: '',
                isJihuo: false,
                warning4: '',
            }
        },
        methods: {
            //激活选科卡
            goJihuo() {
                // 上线前删除
                var token = window.sessionStorage.getItem('ymtxToken');
                // window.sessionStorage.setItem('token',token);
                // console.log(token);
                var XuankekaNumber = this.XuankekaNumber;
                var Xuankekapassword = this.Xuankekapassword;
                var _this = this;
                if(!XuankekaNumber && !Xuankekapassword) {
                    this.warning4="账号或密码不能为空";
                    return;
                }
                this.$ajax.post(this.G_uri + '/chooseSubject/bindBalanceChooseSubjectCard',{
                    card: XuankekaNumber,
                    password: Xuankekapassword
                },{
                    headers:{
                        token: token
                    }
                })
                    .then(function(res) {
                        if(res.data.code == 2000) {
                            // 激活生涯卡成功显示成功弹窗
                            _this.isJihuo = true;

                        }else if(res.data.code == 1016) {
                            _this.$router.push('/login');
                        }else {
                            _this.warning4 = res.data.msg;
                        }

                    })
                    .catch(function(error) {
                        console.log(error);
                        // alert('当前服务器繁忙，请刷新')
                    });
            }
        },
        mounted() {

        },
        created() {

        }
    }
</script>