<template>
<div class="user-index">
  <ul class="banner">
    <li class="user-img">
      <img src="../../assets/images/user/test.jpg"/>
    </li>
    <li class="user-name">测试员</li>
    <li class="user-ip" @click="showIpDia">校长<i class="van-icon van-icon-arrow van-cell__right-icon"></i></li>
  </ul>
  <van-cell-group>
    <van-cell title="修改密码" icon="edit-data" is-link to="/user/changePassword" />
    <van-cell title="查看投诉与建议" icon="records" is-link to="/user/complaints" />
    <van-cell title="退出登录" icon="sign" is-link />
  </van-cell-group>
  <ip-pop></ip-pop>
</div>
</template>
<script>
import IpPop from '../popup/ipPop'
export default {
  components: {
    IpPop
  },
  data () {
    return {
      routerUrl: {
        index: '/index',
        teacher: '/teacher/teacherIndex'
      }
    }
  },
  methods: {
    showIpDia () {
      this.$store.state.ipPopup.ipShow = true
    },
    goTo (url, ip) {
      this.$router.push({path: url, query: {name: ip}})
    }

  }
}
</script>
<style lang="less">
  .user-index{
  .banner{
    width: 100%;
    height: 347px;
    background: #4983f7;
  .user-img{
    width: 117px;
    height: 117px;
    padding: 57px 0 0 0;
    margin: 0 auto;
  }
  .user-img img{
    width: 117px;
    height: 117px;
  }
  .user-name{
    color: #fff;
    font-size: 28px;
    text-align: center;
    padding: 90px 0 20px;
  }
  .user-ip{
    width: 163px;
    height: 54px;
    border-radius:50px;
    margin: 0 auto;
    border: 1px #fff solid;
    text-align: center;
    font-size: 24px;
    line-height: 54px;
    color: #fff;
  }
  }
  .van-cell-group{
    background: #eef1f6
  }
  .van-cell{
    font-size: 26px;
    line-height: 80px;
    margin:30px 0 0 0 ;
    padding: 8px 15px 0;
  }
  .van-cell__left-icon{
    font-size: 28px;
    line-height: 80px;
    margin:0 25px 0 15px;
    color: #4983f7;
  }
  .van-cell__right-icon{
    font-size: 20px;
    line-height: 54px;
  }
  .van-cell__right-icon:before{
    -webkit-transform: rotate(90deg);
    color: #fff;
  }
  }

</style>
