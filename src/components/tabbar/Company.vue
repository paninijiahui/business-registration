<template>
  <div class="tabs">
    <div id="tabbar">

      <div class="header">
        <img height=auto; width="100%"  src="../../assets/img/head.jpg">
      </div>

      <div class="body">

        <div class="a">
          <div class="a01">
            <span class="name" style="position: relative;top: 80px">1.上传营业执照复印件</span> <br />
            <span class="smallFont" style="color:#66667D; position: relative;top:81px;left:-18px;"> 必须是 :
              加盖公司红章后的正面完整清晰照片</span> <br />
            <span class="smallFont" style="position: relative;top:82px;left:-18px;">支持jpg,png,gif,bmp,psd,tiff等图片格式</span>
          </div><br />

          <div class="a02">
            <ul class="idcard-ul">
              <li v-if="imgs.length>0" v-for='(item ,index ) in imgs' class="iu-item">
                <img :src="item" class="iul-img">
              </li>
              <li style="position:relative" v-if="imgs.length>=3 ? false : true" class="iu-img">
                <span class="add-img">+</span><input class="upload" @change='add_img' type="file" accept="image/*">
              </li>
            </ul>
          </div><br />
        </div>

        <div class="b">
          <div class="b01">
            <span class="name">2.&nbsp公司招聘业务负责人或法人名片</span> <br />
            <span class="smallFont" style="color:#66667D;position: relative;left:-18px;">必须是 : 企业目前真实在职的招聘负责人或法人名片
            </span><br />
            <span class="smallFont" style="color: #66667D;position: relative;left:-18px;"> 关键信息需清晰可见。 </span><br />
            <span class="smallFont" style="position: relative;left:-18px;">支持jpg,png,gif,bmp,psd,tiff等图片格式</span>
          </div>
          <div class="b02">
            <ul class="idcard-ul" style="">
              <li v-if="imgs.length>0" v-for='(item ,index ) in imgs' class="iu-item">
                <img :src="item" class="iul-img">
              </li>
              <li style="position:relative" v-if="imgs.length>=3 ? false : true" class="iu-img">
                <span class="add-img">+</span><input class="upload" @change='add_img' type="file" accept="image/*">
              </li>
            </ul>
          </div>
        </div> <br />

        <div class="infos">
          <span class="nameTitle">3. &nbsp &nbsp公司全称 </span>
          <div class="div-bor" style="position: relative;left:300px;top:-22px;">
            <i class="icon-company"></i>
            <input type="text" v-model="fullname" class="company"  style="width: 400px" placeholder="营业执照上的公司名称" />
          </div>
        </div> <br />

        <div class="infos01">
          <span class="nameTitle">4. &nbsp &nbsp社会信用代码 </span>
          <div class="div-bor" style="position: relative;left:300px;top:-22px;">
            <input type="number" v-model.number="credit" style="width: 420px" placeholder="营业执照上面的：统一社会信用代码后面的18位数字字母" />
          </div>
        </div> <br />

        <div>

          <div id="infos02">
            <span style="top:-10px" class="nameTitle"> 5. &nbsp &nbsp所在地  </span>
            <input placeholder="中国" style="top:-10px;width:70px ;position: relative;left:220px" />
            <select v-model="selected" style="top:-10px;width:70px ;position: relative;left:230px">
              <option v-for="yx in YX" :value="yx.text">
                {{yx.text}}
              </option>
            </select>
            <select style="top:-10px;width:70px ;position: relative;left:240px">
              <option v-for="zy in selection" :value="zy.text" :selected="$index == 0 ? true : false">
                {{zy.text}}
              </option>
            </select>
          </div>
        </div> <br />

        <div class="infos03">
          <span class="nameTitle">6. &nbsp &nbsp联系人姓名 </span>
          <div class="div-bor" style="position: relative;left:300px;top:-22px;">
            <i class="icon-name"></i>
            <input type="text"  v-model="people" class="name"  style="width: 400px" placeholder="请填写真实姓名" />
          </div>
        </div> <br />

        <div class="infos04">
          <span class="nameTitle">7. &nbsp &nbsp职位 </span>
          <div class="div-bor" style="position: relative;left:300px;top:-22px;">
            <i class="icon-position"></i>
            <input type="text" v-model="career" class="position"  style="width: 400px" placeholder="请填写联系人目前真实职位" />
          </div>
        </div> <br />

        <div class="infos05">
          <span class="nameTitle">8. &nbsp &nbsp手机 </span>
          <div class="div-bor" style="position: relative;left:300px;top:-22px;">
            <i class="icon-mobile"></i>
            <input type="number" v-model.number="num" style="width: 320px" placeholder="      请填写联系人手机号码" />
            <input placeholder="  获取验证码" style="top:-22px;width:85px ;position: relative;left:340px" />
          </div>
        </div> <br />

        <div class="infos06">
          <span  style="top: -20px" class="nameTitle">9. &nbsp &nbsp接收简历邮箱 </span>
          <div class="div-bor" style="position: relative;left:300px;top:-42px;">
            <i class="icon-email"></i>
            <input type="text"  v-model="qq" class="email"  style="width: 400px" placeholder="请填写贵公司用户接收简历的邮箱" />
          </div>
        </div> <br />

      </div>

      <div class="footer01">
      </div>
      <div class="footer02">
        <img  height="60px" width="800px" src="../../assets/img/buttom02.jpg">
      </div>


    </div>
  </div>
</template>

<script>
  export default {
    name: "Company",
    data() {
      return {
        imgs: [],
        credit: '',
        num: '',
        fullname: '',
        people: '',
        career: '',
        qq: '',
        selected: '北京市',
        YX: [{
          text: '北京市',
          ZY: [{
            text: '昌平区'
          }, {
            text: '朝阳区'
          }, {
            text: "大兴区"
          }, {
            text: "东城区"
          }, {
            text: "房山区"
          }]
        }, {
          text: '上海市',
          ZY: [{
            text: '宝山区'
          }, {
            text: '长宁去'
          }, {
            text: "崇明区"
          }, ]
        }, ]
      }
    },
    methods: {
      add_img(event) {
        let imgData = event.target.files[0];
        if (imgData.name) {
          this.imgs.push(window.URL.createObjectURL(imgData));
        }
      }
    },
    computed: {
      selection: {
        get: function() {
          var that = this;
          return this.YX.filter(function(item) {
            return item.text == that.selected;
          })[0].ZY;
        }
      }
    }
  }
</script>

<style scoped>
  .iul-img {
    width: 100%;
    height: 100%;
  }

  .idcard-ul {
    /*方框的样式*/
    /*display:flex;*/
    position: relative;
    left: 279px;
    top: -29px;
  }

  .iu-item,
  .iu-img {
    /*十字架的长和高（样式）*/
    width: 100px;
    height: 100px;
    border: 1px solid #000;
    display: inline-flex;
    align-items: center;
    position: relative;
    justify-content: center;
    overflow: hidden;
    border-radius: 10px;
    margin: 20px 20px 20px 0;
  }

  .iu-img {
    opacity: 0.5;
  }

  .add-img {
    font-size: 100px;
  }

  .upload {
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    top: 0;
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
    z-index: 999;
    opacity: 0;
    /*background-image: url("../../assets/img/20.jpg");*/
  }

  .div-bor {
    position: absolute;
    width: 200px;
  }

  .icon-company {
    position: absolute;
    left: 0;
    z-index: 5;
    background-image: url("../../assets/img/公司管理.png");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 0px 0px;
    width: 20px;
    height: 20px;
    top: 4px;
    left: 5px;
  }
  .nameTitle {
    position: relative;
    left:20px;
  }
  .company {
    padding-left: 22px;
  }

  .icon-name {
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
    left: 5px;
  }

  .name {
    padding-left: 22px;
  }

  .icon-position {
    position: absolute;
    left: 0;
    z-index: 5;
    background-image: url("../../assets/img/领带.png");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 0px 0px;
    width: 20px;
    height: 20px;
    top: 4px;
    left: 5px;
  }

  .position {
    padding-left: 22px;
  }

  .icon-email {
    position: absolute;
    left: 0;
    z-index: 5;
    background-image: url("../../assets/img/邮箱.png");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 0px 0px;
    width: 20px;
    height: 20px;
    top: 4px;
    left: 5px;
  }

  .email {
    padding-left: 22px;
  }

  .icon-mobile {
    position: absolute;
    left: 0;
    z-index: 5;
    background-image: url("../../assets/img/mobile.png");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 0px 0px;
    width: 20px;
    height: 20px;
    top: 4px;
    left: 5px;
  }

  .mobile {
    padding-left: 22px;
  }

  .tabs {
    background-color: #AFBBCE;
    height: 1500px;
    margin: 0;
    padding: 40px 0 0 0;
  }

  .header {
    display: block;
    width: 800px;
   /* height: 100px;
    position: absolute;
    top: 0;
    background-color: #0A132A;*/
    /*background-image: url("../../assets/img/head.jpg");*/
  }

  #tabbar {
    background-color: #F8F9FE;
    display: block;
    width: 800px;
    margin: 0 auto;
  }

  .body {
    padding: 20px 0;
  }

  .body div {
    font-size: 16px;
    font-weight: normal;
  }

  .smallFont {
    font-size: 10px;
    color: #DCDCDC;
    margin-left: 54px;
  }
  .footer01 {
    display: block;
    width:800px;
    height: 120px;
    background-color: #0A132A;
  }
  .name::after{
    content: "*";
    color: #fa7268
  }
  .nameTitle::after{
    content: "*";
    color: #fa7268
  }
</style>
