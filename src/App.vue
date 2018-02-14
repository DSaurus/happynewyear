<template>
  <div id="app">
    <div class="shadow" v-show="isShadow"></div>
    <div>
      <div>
        <div class="dv_00psd_layer_0"></div>
        <div class="group_0"><div class="dv_00psd_layer_1"></div>
          <div class="dv_00psd_layer_2"></div>
        </div>
        <div class="group_1"><div class="dv_00psd_layer_3"></div>
          <div class="dv_00psd_layer_4"></div>
          <div class="dv_00psd_layer_5"></div>
          <div class="dv_00psd_layer_6"></div>
        </div>
        <div class="group_2"><div class="dv_00psd_layer_7"></div>
          <div class="dv_00psd_layer_8"></div>
          <div class="dv_00psd_layer_9"></div>
          <div class="dv_00psd_layer_10"></div>
          <div class="dv_00psd_layer_11"></div>
        </div>
        <div class="dv_00psd_layer_12"></div>

        <div class="newWay"  v-on:click="newWay" v-show="!isHidden">开启新旅程</div>
        <div class="inputWindow" v-show="isShadow">
          <div class="inputTip">您的名字是？</div>
          <input class="inputText" v-model="theName"/>
          <div class="inputConfirm" v-on:click="theChange">-确定-</div>
        </div>

        <div class="theSaying" v-show="isHidden">
          <div class="firstSaying">亲爱的{{sayingUser}}</div>
          <pre class="mainSaying">{{sayingWords}}</pre>
        </div>


        <div class="group_4"><div class="dv_00psd_layer_46"></div>
          <div class="dv_00psd_layer_47" v-show="!isHidden"></div>
          <div class="dv_00psd_layer_48" v-show="!isHidden"></div>
          <div class="group_5">
            <div class="dv_00psd_layer_49"></div>
            <div class="dv_00psd_layer_50"></div>
            <div class="dv_00psd_layer_51"></div>
          </div>
          <div class="dv_00psd_layer_52"></div>
          <div class="dv_00psd_layer_53"></div>
          <div class="dv_00psd_layer_54"></div>
        </div>
        <div class="dv_00psd_layer_55"></div>
        <div class="dv_00psd_layer_56"></div>
        <div class="dv_00psd_layer_57"></div>
        <div class="dv_00psd_layer_58"></div>
        <div class="dv_00psd_layer_59"></div>
        <div class="dv_00psd_layer_60"></div>
        <div class="dv_00psd_layer_61"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: function () {
    return{
      isShadow: false,
      theName: '',
      isHidden: false,
      sayingList: [],
      sayingUser: '',
      sayingWords: '哇哇哇'
    }
  },
  methods: {
    newWay: function () {
      this.isShadow = true;
    },
    theChange: function() {
      if(this.theName === ''){
        return;
      }
      this.isShadow = false;
      this.isHidden = true;
      var _this = this;
      this.$http.get('/static/saying.json').then(function (res) {
        _this.sayingList = res.body.data;
        _this.afterChange();
      })
    },
    afterChange: function () {
      console.log(this.sayingList);
      this.sayingUser = this.theName;
      var _this = this;
      this.sayingList.forEach(function (value) {
        console.log(value)
        if(value.name === _this.theName){
          _this.sayingWords = value.words;
        }
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.theSaying{
  top:50%;
  position: absolute;
  z-index: 5;
  left: 10rem;
  margin-top: -10.5rem;
  transform: rotate(5.5deg);
}
.firstSaying{
  font-weight: bold;
}
.mainSaying{
  font-size: small;
}
.shadow{
  width: 48rem;
  height: 80rem;
  background-color:#000;
  position:absolute;
  top:50%;
  margin-top:-25%;
  left:0;
  z-index:5;
  opacity:0.4;
  filter: alpha(opacity=30);
  display: block;
}
.newWay{
  transform: rotate(5deg);
  background: rgb(230, 0, 0);
  border-radius: 5px;
  color: white;
  font-size: 1rem;
  padding: 0.1rem 0;
  font-weight: bold;
  z-index: 4;
}
.newWay:hover{
  cursor: pointer;
}
.inputTip{
  font-weight: bold;
  padding: 0.2rem;
  font-size: small;
  color: white
}
.inputWindow{
  position: absolute;
  left:8.22rem;
  margin-top: 8.22rem;
  padding: 1rem;
  z-index: 6;
  background: rgb(220, 0, 0);
  border-radius: 5px;
}
.inputText{
  border: none;
  margin-top: 1rem;
  height: 1.5rem;
  border-radius: 5px;
}
.inputConfirm{
  font-size: small;
  margin-top: 1.5rem;
  color: rgb(220, 0, 0);
  font-weight: bold;
  background: white;
  margin-left: 2.5rem;
  margin-right: 2.5rem;
  border-radius: 5px;
}
.inputConfirm:hover{
  cursor: pointer;
}
.newWay { position: absolute; top:50%; width:6.5rem; height:1.8rem; left:8.22rem; margin-top:10.94999999999999rem; background-size:100% auto; }
.dv_00psd_layer_0 { position: absolute; top:50%; width:35.43rem; height:53.15rem; left:0rem; margin-top:-26.575rem; background:url(./images/dv_00psd_layer_0.png); background-size:100% auto; }
.dv_00psd_layer_1 { position: absolute; top:50%; width:35.43rem; height:53.15rem; left:0rem; margin-top:-26.575rem; background:url(./images/dv_00psd_layer_1.png); background-size:100% auto; }
.dv_00psd_layer_2 { position: absolute; top:50%; width:11.68rem; height:6.28rem; left:23.75rem; margin-top:20.294999999999998rem; background:url(./images/dv_00psd_layer_2.png); background-size:100% auto; }
.dv_00psd_layer_3 { position: absolute; top:50%; width:29rem; height:41.25rem; left:3.65rem; margin-top:-19.265rem; background:url(./images/dv_00psd_layer_3.png); background-size:100% auto; }
.dv_00psd_layer_4 { position: absolute; top:50%; width:4.72rem; height:3.92rem; left:11.66rem; margin-top:-15.264999999999999rem; background:url(./images/dv_00psd_layer_4.png); background-size:100% auto; }
.dv_00psd_layer_5 { position: absolute; top:50%; width:4.26rem; height:8.21rem; left:29.02rem; margin-top:11.754999999999999rem; background:url(./images/dv_00psd_layer_5.png); background-size:100% auto; }
.dv_00psd_layer_6 { position: absolute; top:50%; width:2.56rem; height:3.27rem; left:13.77rem; margin-top:21.805000000000003rem; background:url(./images/dv_00psd_layer_6.png); background-size:100% auto; }
.dv_00psd_layer_7 { position: absolute; top:50%; width:1.86rem; height:1.85rem; left:1.11rem; margin-top:-15.264999999999999rem; background:url(./images/dv_00psd_layer_7.png); background-size:100% auto; }
.dv_00psd_layer_8 { position: absolute; top:50%; width:1.68rem; height:1.66rem; left:2.82rem; margin-top:-18.865rem; background:url(./images/dv_00psd_layer_8.png); background-size:100% auto; }
.dv_00psd_layer_9 { position: absolute; top:50%; width:1.73rem; height:1.71rem; left:31.77rem; margin-top:6.595000000000002rem; background:url(./images/dv_00psd_layer_9.png); background-size:100% auto; }
.dv_00psd_layer_10 { position: absolute; top:50%; width:1.46rem; height:1.64rem; left:26.36rem; margin-top:-25.224999999999998rem; background:url(./images/dv_00psd_layer_10.png); background-size:100% auto; }
.dv_00psd_layer_11 { position: absolute; top:50%; width:21.14rem; height:49.29rem; left:0rem; margin-top:-24.025rem; background:url(./images/dv_00psd_layer_11.png); background-size:100% auto; }
.dv_00psd_layer_12 { position: absolute; top:50%; width:7.82rem; height:14.38rem; left:1.11rem; margin-top:-7.835000000000001rem; background:url(./images/dv_00psd_layer_12.png); background-size:100% auto; }
.dv_00psd_layer_46 { position: absolute; top:50%; width:6.97rem; height:6.05rem; left:6.32rem; margin-top:13.445000000000004rem; background:url(./images/dv_00psd_layer_46.png); background-size:100% auto; }
.dv_00psd_layer_47 { position: absolute; top:50%; width:20.42rem; height:18.14rem; left:8.44rem; margin-top:-10.694999999999999rem; background:url(./images/dv_00psd_layer_47.png); background-size:100% auto; }
.dv_00psd_layer_48 { position: absolute; top:50%; width:1.92rem; height:4.35rem; left:14.13rem; margin-top:-2.0249999999999986rem; background:url(./images/dv_00psd_layer_48.png); background-size:100% auto; z-index: 1;}  .dv_00psd_layer_49 { position: absolute; top:50%; width:13.88rem; height:2.29rem; left:10.54rem; margin-top:6.824999999999999rem;  background-size:100% auto; }
.dv_00psd_layer_50 { position: absolute; top:50%; width:19.68rem; height:2.75rem; left:7.53rem; margin-top:8.004999999999999rem; background:url(./images/dv_00psd_layer_50.png); background-size:100% auto; }
.dv_00psd_layer_51 { position: absolute; top:50%; width:11.74rem; height:2.18rem; left:14.94rem; margin-top:-12.114999999999998rem; background:url(./images/dv_00psd_layer_51.png); background-size:100% auto; z-index: 1; }
.dv_00psd_layer_52 { position: absolute; top:50%; width:6.28rem; height:7.69rem; left:26.03rem; margin-top:-16.255rem; background:url(./images/dv_00psd_layer_52.png); background-size:100% auto; }
.dv_00psd_layer_53 { position: absolute; top:50%; width:14.72rem; height:9.58rem; left:13.51rem; margin-top:12.095000000000002rem; background:url(./images/dv_00psd_layer_53.png); background-size:100% auto; }
.dv_00psd_layer_54 { position: absolute; top:50%; width:7.63rem; height:2.06rem; left:18.73rem; margin-top:-14.514999999999999rem; background:url(./images/dv_00psd_layer_54.png); background-size:100% auto; }
.dv_00psd_layer_55 { position: absolute; top:50%; width:6.2rem; height:6.56rem; left:27.34rem; margin-top:-7.204999999999998rem; background:url(./images/dv_00psd_layer_55.png); background-size:100% auto; }
.dv_00psd_layer_56 { position: absolute; top:50%; width:12.47rem; height:11.92rem; left:0rem; margin-top:14.654999999999998rem; background:url(./images/dv_00psd_layer_56.png); background-size:100% auto; }
.dv_00psd_layer_57 { position: absolute; top:50%; width:8.48rem; height:8.98rem; left:9.53rem; margin-top:15.294999999999998rem; background:url(./images/dv_00psd_layer_57.png); background-size:100% auto; }
.dv_00psd_layer_58 { position: absolute; top:50%; width:26.16rem; height:18.74rem; left:9.27rem; margin-top:-26.575rem; background:url(./images/dv_00psd_layer_58.png); background-size:100% auto; }
.dv_00psd_layer_59 { position: absolute; top:50%; width:7.51rem; height:8.98rem; left:10.37rem; margin-top:-18.615rem; background:url(./images/dv_00psd_layer_59.png); background-size:100% auto; }
.dv_00psd_layer_60 { position: absolute; top:50%; width:32.42rem; height:26.61rem; left:0rem; margin-top:-13.285rem; background:url(./images/dv_00psd_layer_60.png); background-size:100% auto; z-index: 2; }
.dv_00psd_layer_61 { position: absolute; top:50%; width:25.26rem; height:20.53rem; left:9.72rem; margin-top:-19.244999999999997rem; background:url(./images/dv_00psd_layer_61.png); background-size:100% auto; z-index: 2; }

</style>
