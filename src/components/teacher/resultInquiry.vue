<template>
  <div class="result-inquiry">
    <div class="class-tab">
      <calendar-packing></calendar-packing>
      <div class="operation">筛选</div>
    </div>
    <div class="choose-school-zone" @click="showShoolZoneDia">
      <van-cell-group>
        <van-cell title="选择校区" value="潮人部落" is-link />
      </van-cell-group>
    </div>
    <van-radio-group v-model="radio">
    <div class="class-list"  @click="selectFn('1',urls.examinationResult)">
    <div class="class-list-l">
        <van-radio name="1" />
    </div>
    <div class="class-list-r">
      <dl>
        <dt>学习班考试<span class="num">2018.7.27</span></dt>
        <dd>考试项目：语文，数学，英语</dd>
        <dd class="last-item">班级数：<span class="black">0</span>考试人数：<span class="black">4</span>平均分：<span class="yellow">300</span></dd>
      </dl>
    </div>
  </div>
    <div class="class-list"  @click="selectFn('2',urls.examinationResult)">
      <div class="class-list-l">
          <van-radio name="2" />
      </div>
      <div class="class-list-r">
        <dl>
          <dt>学习班考试<span class="num">2018.7.27</span></dt>
          <dd>考试项目：语文，数学，英语</dd>
          <dd class="last-item">班级数：<span class="black">0</span>考试人数：<span class="black">4</span>平均分：<span class="yellow">300</span></dd>
        </dl>
      </div>
    </div>
    <div class="class-list"  @click="selectFn('3',urls.examinationResult)">
      <div class="class-list-l">
          <van-radio name="3" />
      </div>
      <div class="class-list-r">
        <dl>
          <dt>学习班考试<span class="num">2018.7.27</span></dt>
          <dd>考试项目：语文，数学，英语</dd>
          <dd class="last-item">班级数：<span class="black">0</span>考试人数：<span class="black">4</span>平均分：<span class="yellow">300</span></dd>
        </dl>
      </div>
    </div>
    </van-radio-group>
    <bottom-btn :buttonData="buttonData"></bottom-btn>
    <school-pop></school-pop>
  </div>
</template>
<script>
import CalendarPacking from '../general/calendarPacking'
import SchoolPop from '../popup/schoolPop'
import BottomBtn from '../general/bottomBtn'
export default {
  components: {
    SchoolPop,
    BottomBtn,
    CalendarPacking
  },
  data () {
    return {
      value: '',
      radio: '1',
      buttonData: {
        text: '录入成绩',
        url: '/teacher/resultInput'
      },
      urls: {
        examinationResult: '/teacher/examinationResult'
      }
    }
  },
  mounted () {
  },
  methods: {
    onSearch () {
    },
    showShoolZoneDia () {
      this.$store.state.schoolPopup.isShow = true
    },
    goTo (url) {
      this.$router.push({path: url})
    },
    selectFn (value, url) {
      this.radio = value
      this.goTo(url)
    }
  },
  computed : {
    item () {
      return this.$store.state.commentPopup.item
    }
  },
  watch:{
    item :{
      //日期快速切换值
      handler(val){
        this.$toast(val)
      }
    }
  }
}
</script>
<style lang="less">
.result-inquiry{
  .class-tab{
    background: #fff;
    height: 83px;
    border-top:1px #000 solid;
    position: relative;
    padding:10px 20px;
  .list-search-l{
    float: left;
  }
  .van-cell{
    font-size: 26px;
  }
  .van-cell__left-icon{
    font-size: 26px;
    top:15px;
    margin-right: 10px;
  }
  .van-search__action{
    font-size: 26px;
    background: #eff1f6;
    position: relative;
    left:-32px;
    border-radius: 35px;
    padding: 16px 23px;
  }
  .van-search{
    width: 606px;
  }
  .van-search .van-cell{
    border: 1px #eff1f6 solid;
    border-right:none;
    border-top-left-radius: 35px;
    border-bottom-left-radius: 35px;
    padding: 0px 10px;
    line-height: 54px;
  }
  .operation{
    position: absolute;
    right: 20px;
    top: 15px;
    padding: 10px 23px;
    font-size: 26px;
    background: #eff1f6;
    border-radius: 35px;
    margin: 6px 5px 0 0;
  }
  }
  .choose-school-zone{
  .van-cell{
    font-size: 28px;
    line-height: 45px;
    padding: 15px 35px;
  }
  .van-cell__right-icon{
    font-size: 24px;
    line-height: 45px;
    margin-left: 10px;
  }
  }
.class-list{
  padding: 10px 35px;
  background:#fff;
  margin-bottom: 20px;
  height:170px;
.class-list-l{
  float: left;
  width: 60px;
  .van-radio__input{
    height: 5em;
    top:72px;
    font-size: 30px;
  }
.van-radio .van-icon-checked{
  color: #4286ed;
}
}
.class-list-r{
  float: left;
width:600px;
dt{
  font-size: 32px;
  line-height: 64px;
span{
  float: right;
  font-size: 20px;
  color: #838383;
}
}
dd{
  color: #838383;
  line-height: 43px;
}
.last-item{
span{
  color: #000;
  padding-right: 40px;
}
span.yellow{
  color: #f2b30a;
}

}
}
}

.van-popup{
  width: 100%;
}
.ip-list{
  background:#fff ;
  text-align: left;
dt{
  text-align: center;
  font-size: 30px;
  line-height: 100px;
  color: #838383;
}
dd{
  height: 80px;
  line-height: 80px;
  font-size: 28px;
  text-indent: 15px;
  border-bottom:1px #eef1f6 solid ;
}

}

}

</style>
