<template>
    <div class="jihuoka">
        <div class="tanchuang1" v-show="!isJihuo">
            <div class="title">{{title}}卡</div>
            <p class="neirong">
                <input type="text" v-model="card" placeholder="请输入账号" class="Username" >
            </p>
            <!-- <p class="warning">{{warning1}}</p> -->
            <p class="neirong2">
                <input type="password" v-model="password" placeholder="请输入密码" class="Password1">
            </p>
            <p class="warning">{{warning4}}</p>
            <button @click="goJihuo">确定</button>
            <div class="close" @click="$emit('go-back')">
                X
            </div>
        </div>
        <div class="tanchuang2" v-show="isJihuo">
            <div class="tubiao"><img src="/imgs/tongyongtanchuang/chenggong.png" alt=""></div>
            <div class="title">{{title}}卡激活成功</div>
            <p class="tishiyu">可使用{{title}}功能</p>
            <button class="goback" @click="goBack">确定</button>
        </div>
    </div>
</template>
<style type="text/css" lang='less' scoped>
    .jihuoka{
        position: fixed;
        left: 0px;
        top: 0px;
        right: 0px;
        bottom: 0px;
        z-index: 1000000000000;
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
                background: url(/imgs/login/touxiang.png) no-repeat 10px center;
            }
            .Password1 {
                background: url(/imgs/login/mima.png) no-repeat 10px center;
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
        props: [ 'title','url', 'cardAPI' ],
        data() {
            return {
                // 卡账号
                card: '',
                // 卡密码
                password: '',
                isJihuo: false,
                warning4: '',
            }
        },
        methods: {
            goTest() {

            },
            //激活卡
            goJihuo() {
                // 上线前删除
                // this.isJihuo = true;
                // return;

                var token = window.sessionStorage.getItem('ymtxToken');
                window.sessionStorage.setItem('token',token);
                var card = this.card;
                var password = this.password;
                var _this = this;
                var cardAPI = this.cardAPI;
                // var url = this.url;
                this.$ajax.post(this.G_uri + cardAPI,{
                    card: card,
                    password: password
                },{
                    headers:{
                        token: token
                    }
                })
                    .then(function(res) {
                        if(res.data.code == 2000) {    
                        	_this.isJihuo = true;

                        	// window.open(url, "_blank");
                      //   	var a = $("<a target='_blank' href=" + url + "></a>").get(0);
		                    // var e = document.createEvent('MouseEvents');
		                    // e.initEvent('click', true, true);
		                    // a.dispatchEvent(e);
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
            },
            // 购买成功返回进行生涯测评
            goBack() {
                var token = window.sessionStorage.getItem('ymtxToken');
                var _this = this;
                var url = this.url;
                _this.$emit('go-back');
                var a = $("<a target='_blank' href=" + url + "></a>").get(0);
                var e = document.createEvent('MouseEvents');
                e.initEvent('click', true, true);
                a.dispatchEvent(e);
            }
        },
        mounted() {

        },
        created() {

        }
    }
</script>