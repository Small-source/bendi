<template>
    <div class="message">
        <div class="messageContent">
            <div class="title">
                <img src="imgs/careerArchives/icon_biaoti.png" alt="">
                基本信息
            </div>
            <form action="" style="height: 450px">
                <div class="inputs noSelected">
                    <span><i>*</i>姓名:</span>
                    <el-input
                            :value="user.name"
                            :disabled="true">
                    </el-input>
                </div>
                <div class="inputs">
                    <span><i>*</i>性别:</span>
                    <el-select v-model="sex"  placeholder="性别" :disabled="noModify.sex&&true||false">
                        <el-option v-for="(item,$index) in sexs" :key="$index" :label="item" :value="item">
                        </el-option>
                    </el-select>
                </div>
                <div class="inputs noSelected">
                    <span><i>*</i>民族:</span>
                    <el-input type="text" v-model="nation"  :disabled="noModify.nation&&true||false">
                    </el-input>
                </div>
                <div class="inputs">
                    <span><i>*</i>生日:</span>
                    <el-date-picker
                            v-model="birthday"
                            type="date"
                            placeholder="选择日期"
                            :disabled="noModify.birthday&&true||false"
                    >
                    </el-date-picker>
                </div>
                <div class="inputs"></div>
                <div class="inputs"></div>
                <div class="inputs noSelected">
                    <span><i>*</i>省/市:</span>
                    <el-input
                            :value="user.province"
                            :disabled="true">
                    </el-input>
                </div>
                <div class="inputs noSelected">
                    <span><i>*</i>城市:</span>
                    <el-input
                            :value="user.city"
                            :disabled="true">
                    </el-input>
                </div>
                <div class="inputs noSelected">
                    <span><i>*</i>区/县/市:</span>
                    <el-input
                            :value="user.area"
                            :disabled="true">
                    </el-input>
                </div>
                <div class="inputs noSelected">
                    <span><i>*</i>高考年份:</span>
                    <el-input
                            :value="user.baccll_year"
                            :disabled="true">
                    </el-input>
                </div>
                <div class="inputs"></div>
                <div class="inputs"></div>
                <div class="inputs" style="width: 100%">
                    <span>选科情况:</span>
                    <el-checkbox-group style="display: inline-block"
                            v-model="chooseCourseRequire"
                            :max="3">
                        <el-checkbox v-for="(subject,$index) in subjects" :label="subject" :key="$index">{{subject}}</el-checkbox>
                    </el-checkbox-group>
                </div>
                <div class="inputs noSelected">
                    <span><i>*</i>手机号码:</span>
                    <el-input
                            :value="user.username"
                            :disabled="true">
                    </el-input>
                </div>
                <div class="inputs">
                    <span>QQ:</span> <input type="text" v-model="qq">
                </div>
                <div class="inputs">
                    <span>电子邮箱:</span> <input type="text" v-model="email">
                </div>
                <div class="inputs" >
                    <span>政治面貌:</span> <input type="text" v-model="politicalStatus">
                </div>
                <div class="inputs">
                    <span>学生类型:</span> <input type="text" v-model="studentType">
                </div>
                <div class="inputs">
                    <span>外国语种:</span> <input type="text" v-model="foreignLanguage">
                </div>
                <div class="inputs">
                    <span>所在中学:</span> <input type="text" v-model="schoolName">
                </div>
                <div class="inputs">
                    <span>所在班级:</span> <input type="number" v-model="schoolClass" placeholder="请填写数字">
                </div>
                <div class="inputs">
                    <span>担任职务:</span> <input type="text" v-model="position">
                </div>
            </form>
            <div class="title">
                <img src="imgs/careerArchives/icon_biaoti.png" alt="">
                健康状况
            </div>
            <form action="" style="height: 150px;">
                <div class="inputs">
                    <span>左眼视力:</span> <input type="text" v-model="leftEyeVision">
                </div>
                <div class="inputs">
                    <span>右眼视力:</span> <input type="text" v-model="rightEyeVision">
                </div>
                <div class="inputs"></div>
                <div class="inputs">
                    <span>是否色盲:</span>
                    <el-select  v-model="isColorBlindness">
                        <el-option  label="是" value="是"></el-option>
                        <el-option  label="否" value="否"></el-option>
                    </el-select>
                </div>
                <div class="inputs">
                    <span>是否色弱:</span>
                    <el-select v-model="isWeak">
                        <el-option  label="是" value="是"></el-option>
                        <el-option  label="否" value="否"></el-option>
                    </el-select>
                </div>
                <div class="inputs"></div>
                <div class="inputs">
                    <span>身高/cm:</span> <input type="text" v-model="height">
                </div>
                <div class="inputs">
                    <span>体重/kg:</span> <input type="text" v-model="weight">
                </div>
                <div class="inputs">
                    <span>肺活量/ml:</span> <input type="text" v-model="vitalCapacity">
                </div>
            </form>
            <div class="title">
                <img src="imgs/careerArchives/icon_biaoti.png" alt="">
                家庭状况
            </div>
            <form action="" style="height: 96px;">
                <div class="inputs">
                    <span>父亲姓名:</span> <input type="text" v-model="fatherName">
                </div>
                <div class="inputs">
                    <span>手机号码:</span> <input type="text" v-model="fatherPhone">
                </div>
                <div class="inputs">
                    <span>文化程度:</span> <input type="text" v-model="fatherEducationalLevel">
                </div>
                <div class="inputs">
                    <span>行业/职业:</span> <input type="text" v-model="fatherIndustryAndPosition">
                </div>
            </form>
            <form action="" style="height: 96px;margin-top:35px ">
                <div class="inputs">
                    <span>母亲姓名</span> <input type="text" v-model="matherName">
                </div>
                <div class="inputs">
                    <span>手机号码</span> <input type="text" v-model="matherPhone">
                </div>
                <div class="inputs">
                    <span>文化程度:</span> <input type="text" v-model="matherEducationalLevel">
                </div>
                <div class="inputs">
                    <span>行业/职业:</span> <input type="text" v-model="matherIndustryAndPosition">
                </div>
            </form>
            <div class="save" @click="save">
                保存
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        name: "index",
        data(){
            return {
                province:[],
                shi1: [],
                qu1: [],
                city:[],
                block:[],
                sexs:['男','女'],
                isNo:['是','否'],
                years:[],
                baccll_year:"",//高考年份
                chooseCourseRequire:[],//选科情况
                subjects:["物理","化学","生物","思想政治","历史","地理","技术"],
                sex:'',//性别
                birthday:'',//生日
                schoolName:'',//学校名称
                schoolClass:'',//学校班级
                nation:'',//民族
                qq:'',
                email:'',
                politicalStatus:'',//政治面貌
                studentType: '',//学生类型
                foreignLanguage: '',//外语语种
                position:'',//担任职务
                leftEyeVision: '',//左眼视力
                rightEyeVision: '',//右眼视力
                isColorBlindness:'',//是否色盲
                isWeak: '',//是否色弱
                height: '',//身高
                weight:'',//体重
                vitalCapacity: '',//肺活量
                fatherName: '',//父亲姓名
                fatherPhone: '',//父亲手机号
                fatherEducationalLevel: '',//父亲文化程度
                fatherIndustryAndPosition: '',//父亲行业及岗位，
                matherName: '',//母亲姓名
                matherPhone: '',//母亲手机号
                matherEducationalLevel: '',//母亲文化程度
                matherIndustryAndPosition: '',//母亲行业及岗位
                noModify:{}//不可修改信息
            }
        },
        methods:{
            // 加载china地点数据，三级
            getCityData:function(){
                let that = this;
                that.citys.forEach(function(item,index){
                    //省级数据
                    that.province.push({ value: item.name, children: item.cityList})
                })
            },
            // 选省
            choseProvince:function(e) {
                let that = this;
                that.city = [];
                that.block = [];
                that.cname = '';
                that.bname = '';
                for (var index2 in that.province) {
                    if (e === that.province[index2].value) {
                        that.shi1 = that.province[index2].children
                        that.pname = that.province[index2].value
                        that.shi1.forEach(function(citem,cindex){
                            that.city.push({value: citem.name, children: citem.areaList})
                        })
                    }
                }
            },
            // 选市
            choseCity:function(e) {
                let that = this;
                that.block = [];
                for (var index3 in that.city) {
                    if (e === that.city[index3].value) {
                        that.qu1 = that.city[index3].children
                        that.cname = that.city[index3].value
                        that.qu1.forEach(function(bitem){
                            that.block.push({value: bitem, children: []})
                        })
                    }
                }
            },
            // 选区
            choseBlock:function(e) {
                this.bname=e;
            },
            //渲染个人信息
            person(){
                //不可修改信息判断
                this.noModify={
                    sex:this.sexs[this.user.sex-1],
                    nation:this.user.nation,
                    birthday:this.user.birthday
                }
                this.birthday=this.user.birthday
                this.sex=this.sexs[this.user.sex-1]
                this.isColorBlindness=this.isNo[this.user.is_color_blindness-1]
                this.isWeak=this.isNo[this.user.is_weak-1]
                this.schoolName=this.user.school_name
                this.schoolClass=this.user.school_class
                this.birthday=this.user.birthday
                this.nation=this.user.nation
                this.qq=this.user.qq
                this.chooseCourseRequire = this.user.choose_subject||[]
                this.email=this.user.email
                this.politicalStatus=this.user.political_status
                this.studentType=this.user.student_type
                this.foreignLanguage=this.user.foreign_language
                this.position=this.user.position
                this.leftEyeVision=this.user.left_eye_vision
                this.rightEyeVision=this.user.right_eye_vision
                this.height=this.user.height
                this.weight=this.user.weight
                this.vitalCapacity=this.user.vital_capacity
                this.fatherName=this.user.father_name
                this.fatherPhone=this.user.father_phone
                this.fatherEducationalLevel=this.user.father_educational_level
                this.fatherIndustryAndPosition=this.user.father_industry_and_position
                this.matherName=this.user.mather_name
                this.matherPhone=this.user.mather_phone
                this.matherEducationalLevel=this.user.mather_educational_level
                this.matherIndustryAndPosition=this.user.mather_industry_and_position
            },
            //保存个人信息
            save(){
                let _this=this;
                this.$ajax.post(this.G_uri+this.ports.user.modifyUserInfo,{
                    student:{
                        sex:this.sex=='男'?1:2,
                        schoolName:this.schoolName,
                        schoolClass:this.schoolClass,
                    },
                    info:{
                        birthday:this.birthday,
                        nation:this.nation,
                        chooseSubject:this.chooseCourseRequire,
                        qq:this.qq,
                        email:this.email,
                        politicalStatus:this.politicalStatus,
                        studentType:this.studentType,
                        foreignLanguage:this.foreignLanguage,
                        position:this.position,
                        leftEyeVision:this.leftEyeVision,
                        rightEyeVision:this.rightEyeVision,
                        isColorBlindness:this.isColorBlindness=='是'?1:2,
                        isWeak:this.isWeak=='是'?1:2,
                        height:this.height,
                        weight:this.weight,
                        vitalCapacity:this.vitalCapacity,
                        fatherName:this.fatherName,
                        fatherPhone:this.fatherPhone,
                        fatherEducationalLevel:this.fatherEducationalLevel,
                        fatherIndustryAndPosition:this.fatherIndustryAndPosition,
                        matherName:this.matherName,
                        matherPhone:this.matherPhone,
                        matherEducationalLevel:this.matherEducationalLevel,
                        matherIndustryAndPosition:this.matherIndustryAndPosition
                    },
                },{
                    headers:{
                        token: window.sessionStorage.getItem('ymtxToken')
                    }
                }).then((res)=>{
                    if(res.data.code==2000){
                        _this.success();
                    }
                })
            },
            //保存成功提示
            success(){
                this.$message({
                    message: '保存成功！',
                    type: 'success'
                });
                let token= window.sessionStorage.getItem('ymtxToken')
                ///获取个人信息
                this.$store.dispatch({
                    type:'getUserInfo',
                    token:token,
                    vue:this
                });
            }
        },
        computed:{
            citys(){
                return this.$store.state.citys
            },
            user(){
                return this.$store.state.user
            }
        },
        created(){
            let date=new Date();
            let year=date.getFullYear();
            let mounth=date.getMonth()+1;
            let day=date.getDate();
                if(mounth>=7){
                    year+=1
                }
                if(mounth==6&&day>=7){
                    year+=1
                }
                for (let i=0;i<5;i++){
                  this.years[i]=year++
                }
        },
        mounted(){
            this.getCityData();
            this.person();
        },
        watch:{
            citys(){
                this.getCityData();
            },
            user(){
                this.person()
            }
        }
    }
</script>
<style scoped lang="less">
   .message{
       *{
           box-sizing: border-box;
           letter-spacing: 1.5px;
       }
        box-sizing: border-box;
        padding-left:20px;
       .messageContent{
           background: #fff;
           padding: 0 20px 25px;
           img{
               margin-right: 5px;
           }
           .title{
               font-size: 17px;
               color: #348DF1;
               font-weight: bolder;
               padding-top: 24px;
               letter-spacing: 2px;
           }
           p{
               line-height: 62px;
               color:#333333;
           }
           form{
               display: flex;
               flex-wrap: wrap;
               justify-content: space-between;
               align-content: space-between;
               width: 100%;
               margin: 20px 0;
               .inputs{
                   min-width: 284px;

               }
               .noSelected{
                   div{
                       display: inline-block !important;
                       width: 192px;
                       height: 38px;
                   }
               }
               span{
                   display: inline-block;
                   min-width: 80px;
                   text-align: right;
                   margin-right: 12px;
                   font-weight: bolder;
                   i{
                       color:#F80001;
                       position: relative;
                       top:2px;
                       left:-3px;
                   }
               }
               input{
                   width: 192px;
                   height: 38px;
                   border-radius: 3px;
                   border:1px solid #DEDEDE;
                   display: inline-block;
                   text-indent: 10px;
               }
           }
           .save{
               width: 110px;
               height: 42px;
               line-height: 42px;
               text-align: center;
               font-size: 16px;
               color:#FEFFFF;
               background: #3B91F4;
               margin: 40px auto;
               border-radius: 5px;
               cursor: pointer;
           }
       }
    }

</style>
<style lang="less">
    .message{
        .inputs{
            input{
                width: 192px;
                height: 38px;
                border-radius: 3px;
                border:1px solid #DEDEDE;
                display: inline-block;
                text-indent: 10px;
            }
        }
    }
</style>
