<template>
    <!-- 升学途径 其他主流途径 -->
    <!--  (体育单招)-->
    <div class="tiyudanzhao studyway_common_father">
        <div class="banner">
            <img src="/imgs/wayToStudy/main/banner.png" alt="">
        </div>
        <div class="main">
            <h6 class="main_title">什么是体育单独招生</h6>
            <div class="main_box">
                <p>体育单招是部分体育专业单独招生的简称，是指经教育部、国家体育总局批准的部分院校可以对运动训练、武术与民族传统体育(注：原名民族传统体育)专业实行单独招生。</p>
            </div>    
        </div>
        <div class="benefit main">
            <h6 class="main_title">招生项目有哪些？</h6>
            <div class="main_box">
                <p>运动训练专业所设项目为：</p>
                <p><span>冬季项目</span>：速度滑冰、短道速滑、花样滑冰、冰球、冰壶、越野滑雪、高山滑雪、跳台滑雪、自由式滑雪、单板滑雪、冬季两项。</p>
                <p><span>其他项目</span>：射击、射箭、场地自行车、公路自行车、山地自行车、BMX小轮车、击剑、现代五项、铁人三项、马术、帆船、赛艇、皮划艇静水、皮划艇激流回旋、蹼泳、滑水、摩托艇、举重、柔道、摔跤、拳击、跆拳道、田径、游泳、公开水域游泳、跳水、水球、花样游泳、体操、艺术体操、蹦床、技巧、手球、曲棍球、棒球、垒球、足球、篮球、排球、沙滩排球(二人制)、乒乓球、羽毛球、网球、橄榄球、高尔夫球、围棋、国际象棋、登山。</p>
                <p>武术与民族传统体育专业所设项目为：武术套路、散打、中国式摔跤。</p>
            </div>
        </div>
        <div class="main">
            <h6 class="main_title">报考条件是什么？</h6>
            <div class="main_box">
               <p>考生须具备以下条件方可报名</p>
               <p>1.符合当年高考报名条件；</p>
               <p>2.具备上述所列项目之二级运动员(含)以上运动技术等级称号。</p>
               <p>考生必须参加生源所在地省级招生考试机构组织的高考报名（具体按各省级招生考试机构要求执行）。</p>
            </div>   
        </div>
        <div class="main">
            <h6 class="main_title">如何参加考试？</h6>
            <div class="main_box">
               <p>考生须具备以下条件方可报名：</p>
               <p>1.符合当年高考报名条件；</p>
               <p>2.具备上述所列项目之二级运动员(含)以上运动技术等级称号。</p>
               <p>考生必须参加生源所在地省级招生考试机构组织的高考报名(具体按各省级招生考试机构要求执行)。</p>
            </div>   
        </div>
        <div class="main">
            <h6 class="main_title">录取要求</h6>
            <div class="main_box">
               <p>（1）在文化成绩不低于180分、专业成绩不低于40分的基础上，各招生院校根据本校实际情况综合确定本校文化成绩和专业成绩录取控制线。</p>
               <p>（2）在达到院校最低录取控制线的基础上，各招生院校根据考生的文化成绩(折合百分制后)和体育专项成绩3：7的比例进行综合评价，计算考生录取综合分。具体公式：综合分=(文化成绩/6)*30%+体育专项成绩*70%。</p>
               <p>（3）具备一级运动员等级资格的考生，其文化考试成绩可在原始分基础上增加30分；具备运动健将技术等级资格的考生，其文化考试成绩可在原始分基础上增加50分。</p>
            </div>   
        </div>
        <div class="remind main">
            <h6 class="main_title">特别提醒</h6>
            <div class="main_box">
                <p><span>1</span>在招生院校原则上依据本校录取率确定分项目招生计划数，上线考生依据填报的志愿梯次顺序，按照综合分由高到低，优先录取一志愿，未完成招生计划的院校，再录取二志愿。</p>
                <p><span>2</span>考生若已被运动训练、武术与民族传统体育专业录取，则不再参加普通高考及高校高水平运动队的录取。</p>
            </div>   
        </div>
        <div class="universities main">
            <h6 class="main_title">
                各省招生计划 
                <span>*由于各方面条件不断调整变化，请考生以各省考试院公布的最新消息为主</span>
            </h6>
            <div class="school_box"  v-for="(item, index) in universities" :key="index">
                <p class="school_title">{{item.title}}</p>
                <ul>
                    <li v-for="(school, index) in item.schoolName" :key="index" @click="goUniversity(school)">{{school}}</li>
                </ul>
            </div>    
        </div>
    </div>
</template>
<script>

export default {
    // components: { Yuanxiaoku },
    // props: [ 'message' ],
     data() {
        return {
            universities: [     
                { title: '运动训练', schoolName: ["北京体育大学","上海体育学院","武汉体育学院","西安体育学院","成都体育学院","内蒙古大学","沈阳体育学院","首都体育学院","天津体育学院","河北体育学院","吉林体育学院","湖南人文科技大学","哈尔滨体育学院","南京体育学院","山东体育学院","广州体育学院","北京师范大学","广西大学","河北师范大学","山西大学","中北大学","山西师范大学","内蒙古师范大学","青海民族大学","内蒙古民族大学","辽宁师范大学","沈阳师范大学","大连大学","大连理工大学(盘锦校区)","宁夏大学","渤海大学","辽宁工程技术大学","吉林大学","东北师范大学","吉林师范大学","新疆师范大学","延边大学","北华大学","长春师范大学","哈尔滨师范大学","华东师范大学","石河子大学","苏州大学","中国矿业大学","江苏师范大学","浙江大学","宁波大学","张家口学院","绍兴文理学院","安徽师范大学","合肥师范学院","福建师范大学","集美大学","陕西师范大学","华东交通大学","南昌大学","江西师范大学","井冈山大学","赣南师范大学","陕西理工学院","宜春学院","中国海洋大学","山东理工大学","烟台大学","聊城大学","西北师范大学","曲阜师范大学","河南大学","郑州大学","河南师范大学","洛阳师范学院","天水师范学院","南阳师范学院","黄河科技学院","华中师范大学","江汉大学","中南大学","青海师范大学","湖南大学","湖南师范大学","湖南工业大学","衡阳师范学院","华南理工大学","云南师范大学","华南师范大学","深圳大学","嘉应学院","广西师范大学","海南师范大学","贵州师范大学","西南大学","重庆师范大学","西华师范大学"]},   
                { title: '武术与民族传统体育', schoolName: ["北京体育大学","上海体育学院","武汉体育学院","西安体育学院","成都体育学院","云南民族大学","沈阳体育学院","首都体育学院","天津体育学院","河北体育学院","吉林体育学院","西北师范大学","哈尔滨体育学院","南京体育学院","山东体育学院","广州体育学院","天津师范大学","宁夏大学","河北师范大学","山西师范大学","晋中学院","内蒙古民族大学","沈阳师范大学","青海师范大学","东北师范大学","哈尔滨师范大学","苏州大学","扬州大学","江苏师范大学","青海民族大学","浙江大学","杭州师范大学","阜阳师范学院","集美大学","江西师范大学","云南师范大学","山东师范大学","鲁东大学","菏泽学院","河南大学","郑州大学","贵州师范大学","河南理工大学","洛阳师范学院","商丘师范学院","黄河科技学院","吉首大学","西南民族大学","广西师范大学","海南师范大学"]}    
            ]
        }
    },
    methods: {
        goUniversity(id) {
            var id = id;
            let {href}=this.$router.resolve({
                path: '/explore/yuanxiaoxiangqing',
                name: '院校详情',
                query: {
                    id: id,
                }
            })
            window.open(href, '_blank');
        }
    },
    created() {
        this.getZizhuzhaoshengList();
    }
}
</script>
<style type="text/css" lang='less' scoped>
    @import "../study_way_common.less";
    .tiyudanzhao {
        .universities {
            .school_box {
                ul li {
                    &:nth-child(8n-1),&:nth-child(8n-2),&:nth-child(8n-3),&:nth-child(8n) {
                        background-color: #e6f8ff;
                    }
                }   
            }
        }
    }
</style>