<template>

  <div class="pc-page zhuyiliceping">
    <div class="test_main test_main_2">
      <rzqnNav></rzqnNav>
      <div class="ques-wrapper test_detail test_detail_ing">
        <div v-if="tip==0" class="fl">从画有不同树木圆圈的小方格内找出4个圆圈小方格，找到后请在该方格上画“✔”
        </div>
        <div class="timebox fr" v-if="tip==0">
          剩余时间：
          <div class="time">
            {{timeTip}}
          </div>
        </div>
        <div class="ques-container box d-relative">
            <div class="ques-answer">
              <div class="zhuti" :style="{width:kuan+'px'} ">
              <div>
            </div>
          </div>
          <div class="bottom next clearfix" style="position: absolute;bottom: 30px;width: 100%;">
            <a href="javascript:;" style="margin:0 auto;" class="btn btn_start" @click="submit">提交</a>
          </div>
          <div class="box" v-if="tip==1"  @click="clickStart">
            <em class="icon part_start"></em>
            <div class="btngroup">
              <a href="javascript:;" class="btn btn_start">点击鼠标开始测试</a>
            </div>
          </div>
        </div>
      </div>
      </div>
    </div>
  </div>
</template>
<script>
  import rzqnNav from '../../../../../components/rzqn.vue';
  import tip from '../../../../../components/tip.vue';
  export default {
    data() {
      return {
        // tip: 1,
        tip: 0,
        questions: [
        ],
        tempTimeStart: '',
        tempTime: '',
        quesArr: [],
        quesEq: 0,
        efficiency: '', // 效率 反应时/正确率
        time: '',
        startTime: '',
        endTime: '',
        answer: 0,
        bar: 0,
        answers: [],
        info_time: '',
        info_correct_rate: '',
        info_efficiency: '',
        type: this.$route.query.type,
        errorTip: '',
        errorClick: 0,
        timeFn: '',
        rightTime1: '',
        rightTime2: '',
        leftTime: 0,
        arrLength: 30,
        timeTip: '',
        imgNumbers:[],
        test:"",
        kuan:""
      }
    },
    mounted() {
        $('.test_menu .item').eq(8).addClass('item_2');
    },
    updated() {

    },
    components: {rzqnNav, tip},
    methods: {
      clickStart: function () {
          if (this.type == 'test') {
              this.timeTip ="0:10";
              this.leftTime=10;
              this.imgNumbers = this.imgNumbers1;
          }else{
              this.timeTip = "3:00";
              this.leftTime=180;
              this.imgNumbers = this.imgNumbers2;
          }
          this.t=null;
        var _this = this;
          $('.info-arrow').hide();
          this.tip=0;
      },
        /**
         * 秒转换为分钟格式
         */
        secondToMin: function (second) {
            var min, sec;
            if (second > 0) {
                sec = second % 60;
                min = parseInt(second / 60);
                if (sec < 10) {
                    sec = '0' + sec;
                }
                this.timeTip = min + ':' + sec + '';
            }
        },
        //答题
        clickQuestion:function(e){
            if(!$(e.target).parent().hasClass('duigou')){
                $(e.target).parent().addClass('duigou')
            }
        },
        /**
       * 提交
       */
      submit: function () {
          clearInterval(this.t)
          if(this.type=='test'){
              this.$router.push('/shengyaceping/rzqn/success/142?type=test')
              return
          }
          this.$router.push('/shengyaceping/rzqn/success/142')
          let _this=this;
        // this.$ajax.post("/api/result/cognition/info/add", {
        //   },
        //   {
        //     headers: {
        //     }
        //   },
        //   {
        //     emulateJSON: true
        //   }
        // ).then(
        //   function (res) {
        //     // 请求成功的结果
        //     var data = res.data;
        //     if (data.code == 0) {
        //       _this.saveNode(2, 21);
        //       _this.$router.push('/shengyaceping/rzqn/success/1')
        //     } else {
        //       _this.layerMsg(data.msg);
        //     }
        //   },
        //   function (res) {
        //       _this.layerMsg('网络错误,请重新提交');
        //   }
        // )
      },
    }
  }
</script>
<style lang='less'>
  .zhuyiliceping{
    .layer {
      top: 120px;
    }
    .evalu-nav {
      background: #333;
      opacity: 1;
    }
    .ques-answer-tip {
      position: absolute;
      top: 0px;
      left: 0px;
      background: #f9f9f9;
      z-index: 10;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #ff3333;
      font-size: 40px;
      width: 100%;
      height: 100%;
      border: 10px solid #fff;
      box-sizing: border-box;
    }
    .errorTip {
      position: absolute;
      z-index: 999;
      width: 100%;
      height: 40px;
      line-height: 40px;
      text-align: center;
      color: #fff;
      top: 50%;
      margin-top: -12.5px;
      left: 0;
      font-size: 25px;
    }
    .fl{
      font-size: 16px;
      color: #666666;
      line-height: 50px;
      position: absolute;
      top: 40px;
      z-index: 10000000;
      left:40px;
      background:#fff;
    }
    .imgs{
      width: 25px;
      height: 25px;
      margin-right:5px;
    }
    .duigou:after{
      position: absolute;
      left: 50%;
      top: 50%;
      display: block;
      content: ' ';
      width: 58px;
      height: 58px;
      margin-left: -29px;
      margin-top: -29px;
      background: url("~@/assets/newceping/duigou.png") center center no-repeat;
    }
    .zhuti{
      margin: 150px auto;
      width: 550px;
      display: flex;
      justify-contsent: space-between;
      flex-wrap: wrap;
      .one{
        width: 16.66%;
        text-align: center;
        position: relative;
        margin-bottom: 20px;
        text-align: center;
      }
      .two{
        width: 6.66%;
        text-align: center;
        position: relative;
        margin-bottom: 20px;
        text-align: center;
        img{
          width: 45px;
        }
      }
      img{
        cursor: pointer;
        position: relative;
        cursor: pointer;
      }
    }
  }

</style>
