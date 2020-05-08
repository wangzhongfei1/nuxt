<template>
    <div>
        <ul>
            <li v-for="data in datalist" :key="data.id">
            <div class="leftInfo">
                <img :src="data.img | imgURL" />
                <div class="content">
                    <div class="filmName">{{data.nm}}</div>
                    <p class="like"><span>{{data.wish}}</span>人想看</p>
                    <p class="filmactor line-ellipsis">主演：{{data.star}}</p>
                    <p> 2020-06 上映</p>
                </div>
            </div>
            <div class="rightButton">
            <button class="btn">想看</button>
            </div>
            </li>
        </ul>
    </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
Vue.filter('imgURL', function(path) {
    return path = path.replace('w.h', '128.180')
})
export default {
    asyncData(data) {
        return axios.get(process.server ? 'https://m.maoyan.com/ajax/moreComingList?ci=65&token=&limit=10&movieIds=342485%2C1241850%2C1283276%2C1286060%2C1236599%2C1212559%2C341890%2C1282454%2C1298349%2C1203734&optimus_uuid=D0EC4EA08F7311EA92D7A7093D0AD1C8AE82D8886EA7478AA5B7AB23C8A9C2AC&optimus_risk_level=71&optimus_code=10' : '/ajax/moreComingList?ci=65&token=&limit=10&movieIds=342485%2C1241850%2C1283276%2C1286060%2C1236599%2C1212559%2C341890%2C1282454%2C1298349%2C1203734&optimus_uuid=D0EC4EA08F7311EA92D7A7093D0AD1C8AE82D8886EA7478AA5B7AB23C8A9C2AC&optimus_risk_level=71&optimus_code=10').then(res => {
            return {
                datalist: res.data.coming
            }
        })  
    }
}
</script>
<style lang="scss" scoped>
ul {
  li {
    overflow: hidden;
    padding: 12px;
    display: flex;
    img {
      float: left;
      width: 64px;
    }
    .content {
      margin-left: 74px;
      font-size: 14px;
      .filmName {
      color: #333;
      font-weight: 700;
      font-size: 17px;
      margin-bottom: 5px;
    }
    .like {
        height: 22px;
        span {
            color: #faaf00;
            font-weight: 700;
        }
    }
    .filmactor {
        height: 22px;
    }
    }
    .leftInfo {
        flex: 4;
    }
    .rightButton {
        flex: 1;
        .btn {
            width: 50px;
            height: 30px;
            background-color: #faaf00;
            border: 0;
            color: #fff;
            margin-top: 20px;
            border-radius: 5px;
        }
    }
    
  }
}
</style>