<template>
	<div class="tabs">
		<div id="tab-bar">
			<div class="header">
        <img height=auto width="100%" src="../../assets/img/head.jpg">
			</div>

			<div class="a1">

				<div>
					<span class="name01">企业注册码</span>
					<input v-model="message01" style="width:470px;height:26px;margin-left: 6px">
				</div>

        <div class="infos01" style="position:relative;top:25px">
          <span class="name">企业名称</span>
          <input v-model="message02" placeholder="如 ： 宁波智士网络技术有限公司" style="width:470px;margin-left: 16px;height:26px">
        </div>

				<div style="position: relative;top: 25px">
					<span class="name" style="position: relative;top: 25px">企业对外简称</span>
					<input v-model="message03" placeholder="如 ： 宁波智士网络" style="position: relative;top: 25px ;width:470px;margin-left: -16px;height:26px"><br />
					<span class="smallFont" style="position: relative;top: 15px">0/1～5</span>
				</div>

				<hr style=" position: relative; top:55px; height:2px;border:none;border-top:2px solid #83988a;" />

				<div style="position:relative;top:65px">
					<span class="name">职位名称</span>
					
					<input v-model="message04" style="width:470px;margin-left: 16px;height:26px">
					<br />
					<span style="position: relative;top: -10px" class="smallFont" >0/2～10</span>
				</div>

				<div style="position:relative;top:65px">
					<span class="name01">职能职业</span>
					
					<input v-model="message05" style="width:470px;margin-left: 24px;height:26px">
					<br />
					<span  style="position: relative;top: -10px" class="smallFont">0/2～10</span>
				</div>

        <div class="name" style="position:relative;top:65px">
          <span >工作类型</span>

          <select name="abc" id="" v-model="job" style="width:480px;margin-left: 108px;height:36px;">
            <option value="全职">全职</option>
            <option value="兼职">兼职</option>
            <option value="实习生">实习生</option>
            <option value="无固定时间">无固定时间</option>
            <option value="小时工日结">小时工日结</option>
            <option value="临时工">临时工</option>
          </select>
        </div>

        <div style="position:relative;top:65px">
          <span  class="name">招聘人数</span>
          <input type="number" v-model.number="num" placeholder="人" style="text-align: right;top:65px;width:470px;margin-left: 16px;height:26px">{{num}}
          <br />
          <span style="position: relative;top: -10px" class="smallFont" >请输入1～1000的数字</span>
        </div>

        <div>
          <span class="name" style="position: relative; top:-22px;">职位描述</span>

          <textarea v-model="message06" placeholder="注：要求中请勿填写涉及歧视的内容，例如：残疾，乙肝等" style="position: relative;top: 80px;text-align: right;width:470px;margin-left: 16px;height:120px;"></textarea>
          <br />
          <span  class="smallFont" style="position: relative; top:-22px;">职位的详细内容和要求</span>
        </div>

        <div style="position:relative;top:75px">
          <span  class="name">工作薪资最低</span>
          <input type="number" v-model.number="money" placeholder="千元" style="text-align: right;width:107px;height:26px">
          <span style="position: relative;left:56px;">—最高</span>
          <input type="number" v-model.number="money" placeholder="千元" style="text-align: right;width:107px;position: relative;left:111px;height:26px">
          <br />
          <p class="smallFont" style="width:170px;color:#66667D;position: relative;top:-20px;">注：请输入月薪范围，最大薪资不能超过最小薪资的3倍。如：3-6千元 </p>
          <span class="smallFont" style="position: relative;top:-36px;">请输入3～100的数字</span>

          <span class="smallFont" style="position: relative;top:-82px;left:186px">请输入3～100的数字</span>
        </div>

        <div style="position:relative;top:50px" >
          <span class="name">职位福利</span>

          <input v-model="message07" placeholder="如 : 提供住宿，缴纳五险，缴纳五险一金" style="width:470px;margin-left: 16px;height:36px">
        </div>

        <div style="position:relative;top:65px">
          <span class="name">工作经验</span>

          <select name="abc" id="" v-model="experience" style="width:480px;margin-left: 16px;height:36px">
            <option value="不限">不限</option>
            <option value="应届生">应届生</option>
            <option value="1～3">1～3</option>
            <option value="3～5">3～5</option>
            <option value="5～10">5～10</option>
            <option value="10年以上">10年以上</option>
          </select>
        </div>

        <div style="position:relative;top:85px">
          <span class="name">学历要求</span>

          <select name="abc" id="" v-model="education" style="width:480px;margin-left: 16px;height:36px">
            <option value="不限">不限</option>
            <option value="初中">初中</option>
            <option value="中专">中专</option>
            <option value="高中">高中</option>
            <option value="大专">大专</option>
            <option value="本科">本科</option>
            <option value="硕士">硕士</option>
            <option value="博士">博士</option>
          </select>
          <br />
          <span style="position: relative;top: -12px" class="smallFont">最低学历要求</span>
        </div>

        <div>
          <span  style="position:relative;top:85px"class="name01">语言要求</span>

          <select v-on:change="change()" v-model="jjid" style="width:150px;position:relative;left:24px;top: 85px;height: 36px;">
            <option value="0">请选择</option>
            <option v-for="ji in crr" :value="ji.jid">{{ji.jname}}</option>
          </select>

          <select name="cid" v-model="ccid" style="width:150px;position:relative;left:26px;top: 85px;height: 36px;">
            <option value="0">-请选择-</option>
            <option v-for="cla in brr" :value="cla.cid">{{cla.cname}}</option>
          </select>
        </div>

        <div style="position:relative;top:100px">
          <span class="name01">其他要求</span>

          <input v-model="message08" placeholder="如 : 技能、证书、操作系统等。" style="width:470px;margin-left: 22px;height: 36px;position: relative;top:5px">
        </div>

        <div>
          <div style="position:relative;top:120px" class="div-bor01">

            <span class="name">工作地点</span>
            <input placeholder="中国" style="width:70px;margin-left: 16px;height: 26px"/>
            <select name="abcd" id="" v-model="city" placeholder="请选择" style="width:70px;margin-left: 1px;height: 32px;">
              <option value="北京市">北京市</option>
              <option value="香港">香港</option>
              <option value="上海市">上海市</option>
              <option value="天津市">天津市</option>
              <option value="河北省">河北省</option>
              <option value="山西省">山西省</option>
              <option value="内蒙古">内蒙古</option>
              <option value="辽宁省">辽宁省</option>
              <option value="吉林省">吉林省</option>
              <option value="黑龙江省">黑龙江省</option>
              <option value="江苏省">江苏省</option>
              <option value="浙江省">浙江省</option>
              <option value="安徽省">安徽省</option>
              <option value="福建省">福建省</option>
              <option value="江西省">江西省</option>
              <option value="山东省">山东省</option>
              <option value="河南省">河南省</option>
              <option value="湖北省">湖北省</option>
              <option value="湖南省">湖南省</option>
              <option value="广东省">广东省</option>
              <option value="广西">广西</option>
              <option value="海南省">海南省</option>
              <option value="重庆市">重庆市</option>
              <option value="四川省">四川省</option>
              <option value="贵州省">贵州省</option>
              <option value="云南省">云南省</option>
              <option value="西藏">西藏</option>
              <option value="陕西省">陕西省</option>
              <option value="甘肃省">甘肃省</option>
              <option value="青海省">青海省</option>
              <option value="宁夏">宁夏</option>
              <option value="新疆">新疆</option>
              <option value="台湾省">台湾省</option>
              <option value="澳门">澳门</option>

            </select><br>
            <div style="margin-top: 7px;">
              <input v-model="message09" placeholder="详细地址" style="width:340px;margin-left: 230px;height: 26px;">
              <input v-model="message10" placeholder="邮编" style="width:122px;margin-left: 0px;height: 26px">
            </div>
          </div>
        </div>

        <div style="position:relative;top:120px"class="name">
          <span >面试地点</span>

          <input style="margin-left: 110px;position:relative;top: 8px; ;height: 26px" type="radio" id="place01" name="place" value="同工作地点" v-model="place">
          <label for="place01">同工作地点</label>
          <input style="position: relative;margin-left: 150px" type="radio" @click="isUser = !isUser" id="place02" name="place" value="其他" v-model="place">
          <label for="place02">其他</label>
          <input type="text" v-model="message11" style="position: relative;margin-left: -5px;" >
        </div>

        <div style="position: relative;top: 112px">
          <span class="name" >面试安排</span>

          <input  style="position: relative;margin-left: 16px" type="checkbox" value="周一" v-model="week">周一
          <input style="position: relative;margin-left: 75px" type="checkbox" value="周二" v-model="week">周二
          <input style="position: relative;margin-left: 75px" type="checkbox" value="周三" v-model="week">周三
          <input style="position: relative;margin-left: 75px" type="checkbox" value="周四" v-model="week">周四
          <input  style="position: relative;margin-left: 230px" type="checkbox" value="周五" v-model="week">周五
          <input style="position: relative;margin-left: 75px" type="checkbox" value="周六" v-model="week">周六
          <input  style="position: relative;margin-left: 75px" type="checkbox" value="周日" v-model="week">周日
        </div>

        <div style="position:relative;top:130px" >
          <span class="name">开始面试</span>
          <select name="a" id="" v-model="time0" style="width:100px;margin-left: -76px;height: 36px">
            <option value="8:30">8:30</option>
            <option value="9：00">9:00</option>
            <option value="9：30">9:30</option>
            <option value="10:00">10：00</option>
            <option value="10:30">10:30</option>
            <option value="11:00">11:00</option>
            <option value="11:30">11:30</option>
            <option value="12:00">12:00</option>
            <option value="12:30">12:30</option>
            <option value="13:00">13:00</option>
            <option value="13:30">13:30</option>
            <option value="14:00">14:00</option>
            <option value="14:30">14:30</option>
            <option value="15:00">15:00</option>
            <option value="15:30">15:30</option>
            <option value="16:00">16:00</option>
            <option value="16:30">16:30</option>
            <option value="17:00">17:00</option>
            <option value="17:30">17:30</option>
          </select>
        <!--  <span style="position: relative;left:56px;">—最高</span>-->
          <span class="name" style="position: relative;margin-left: 170px;top: -4px;">结束面试</span>
          <select name="a" id="" v-model="time1" style="width:100px;position: relative; margin-left: -76px;height: 36px;top: -2px;">
            <option value="8:30">8:30</option>
            <option value="9：00">9:00</option>
            <option value="9：30">9:30</option>
            <option value="10:00">10：00</option>
            <option value="10:30">10:30</option>
            <option value="11:00">11:00</option>
            <option value="11:30">11:30</option>
            <option value="12:00">12:00</option>
            <option value="12:30">12:30</option>
            <option value="13:00">13:00</option>
            <option value="13:30">13:30</option>
            <option value="14:00">14:00</option>
            <option value="14:30">14:30</option>
            <option value="15:00">15:00</option>
            <option value="15:30">15:30</option>
            <option value="16:00">16:00</option>
            <option value="16:30">16:30</option>
            <option value="17:00">17:00</option>
            <option value="17:30">17:30</option>
          </select>
        </div>

        <div style="position:relative;top:140px">
          <span class="name" style="position: relative;top: 3px;">面试联系人</span>

          <div class="div-bor">
            <i class="icon-user"></i>
            <input type="text" class="user" style="margin-left: 10px; width:450px;height: 26px;position: relative;top: -2px;" />
          </div>
        </div>


        <div style="position:relative;top:132px">
          <span class="name" style="position: relative;top: 3px;">联系人手机</span>

          <div class="div-bor">
            <i class="icon-mobile"></i>
            <input type="text" class="mobile" style="margin-left: 10px;width:450px;height: 26px;position: relative;top: -2px;" />
          </div>
        </div>

        <div style="position:relative;top:140px">
          <span class="name01" style="position: relative;top:-61px;">面试备注 </span>
          <textarea v-model="message12" placeholder="如 : 周一到周五9点到12点可面试，须携带本人身份证" style="position: relative;margin-left: 20px;text-align: left;width:470px;height:70px;"></textarea>
          <!-- <span>输入的信息:{{ message }}</span>--><br />
          <span class="smallFont" style="width:170px;color:#66667D;position: relative;top:-59px;" >面试安排及特别说明事项</span>

        </div>

      </div>
      </div>

    <div class="footer01" style="position: relative;top: 150px;left: 100px">
    </div>

	</div>
</template>

<script>
	export default {
		name: "TabBar",
		data() {
			return {
				message01: '',
				message02: '',
				message03: '',
				message04: '',
				message05: '',
				message06: '',
				message07: '',
				message08: '',
				message09: '',
				message10: '',
				message11: '',
				message12: '',
				job: '全职',
				num: '',
				money: '',
				experience: '不限',
				education: '不限',
				city: '',
				place: '同工作地点',
				week: [],
				time0: '11:00',
				time1: '8:30',
				isUser: false,
				trigger: '',
				bindValue: '',
				showConcatenate: true,
				ccid: "0", //学生表的外键
				brr: [], //二级联动班级
				jjid: "0", //班级表的外键
				crr: [] //二级联动级部
				/* triggerList: [
				   {
				     value: 'first',
				     label: '第一'
				   },
				   { value: 'second',
				     label: '第二'
				   },
				   {
				     value: 'third',
				     label: '第三'
				   },
				   {
				     value: '不限',
				     label: '不限'
				   }
				 ],
				 valueList: [
				   {
				     value: 'first',
				     label: '第一'
				   },
				   { value: 'second',
				     label: '第二'
				   },
				   {
				     value: 'third',
				     label: '第三'
				   },
				   {
				     value: '不限',
				     label: '不限'
				   }
				 ]*/
			}
		},
		mounted() { //待domcoument结构加载完毕  自动执行里面的方法
			this.ji();
		},
		methods: { //自定义方法
			/*triggerValue(){
			  console.log('第一级: $(this.trigger)');
			  this.showConcatenate = this.trigger == '不限' ? false : true
			  this.bindValue = '';
			}*/
			/* ji: function () {
			   //查询级部的数据
			   $.post("/db/getji", {}, function (data) {
			     var len = data.length;
			     vm.crr = [];
			     for (var i = 0; i < len; i++) {
			       vm.crr.push(data[i]);//给数组填数据
			     }
			   })
			 },
			 change: function () {
			   var jjid = this.jjid;
			   //查询班级的数据
			   $.post("/db/getcla", {jjid: jjid}, function (data) {
			     var len = data.length;
			     vm.brr = [];//清空数据
			     for (var i = 0; i < len; i++) {
			       vm.brr.push(data[i]);
			     }
			   })
			 }*/
		}
	}
</script>

<style scoped>
	.tabs {
		background-color: #AFBBCE;
		height: 1500px;
		margin: 0;
		padding: 40px 0 0 0;
	}
	.smallFont {
		font-size:10px;
		color:#DCDCDC;
		margin-left:54px;
	}
	.name {
		line-height: 20px;
		display: inline-block;
		margin: 16px 86px 0 53px;
	}
  .name01 {
    line-height: 20px;
    display: inline-block;
    margin: 16px 86px 0 53px;
  }
	.footer01 {
		display: block;
		width:800px;
		height: 80px;
		background-color: #0A132A;
	}
	.header {
		display: block;
		width:800px;
		/*height: 80px;
		background-color: #0A132A;*/
    /*background-image: url("../../assets/img/head.jpg");*/
	}
	#tab-bar {
		/*display: flex;*/
		background-color: #F8F9FE;
		display: block;
		width: 800px;
		margin: 0 auto;
	}
	.a1 {
		padding: 20px 0 ;
	}
	.a1 div {
		font-size: 16px;
		font-weight: normal;

	}
  .div-bor {
    position: relative;
    top:-19px;
    left: 219px;
    width: 200px;
  }

  .icon-user {
    position: absolute;
    left: 0;
    z-index: 5;
    background-image: url("../../assets/img/user.svg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 0px 0px;
    width: 20px;
    height: 20px;
    top: 4px;
    left: 15px;
  }
  .user {
    padding-left: 22px;
  }
  .icon-mobile {
    position: absolute;
    left: 0;
    z-index: 10;
    background-image: url("../../assets/img/mobile.png");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 0px 0px;
    width: 20px;
    height: 20px;
    top: 4px;
    left: 15px;
  }

  .mobile {
    padding-left: 22px;
  }

  .name::after{
    content: "*";
    color: #fa7268
  }

</style>
