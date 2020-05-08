<template>
    <div>
        <ul>
            <li v-for="data in datalist" :key="data.id" @click="handleClick(data.id)">
                <div><img :src="data.img | imgURL" /></div>
                <div class="content">
                    <div class="filmName">{{data.nm}}</div>
                    <p class="filmScore">观众评分： <span>{{Math.floor(Math.random() * 10 + 1)}}</span> 分</p>
                    <p class="filmactor line-ellipsis">主演：{{data.star}}</p>
                    <p>中国大陆 | 100分钟</p>
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
    data() {
        return {
            datalist: []
        }
    },
    methods: {
        handleClick(id) {
            this.$router.push(`/detail/${id}`)
        }
    },
    asyncData() {
        // process.server判断是否在服务器端运行的
        return axios.get(process.server ? 'https://m.maoyan.com/ajax/moreComingList?ci=65&token=&limit=10&movieIds=344450%2C346210%2C1216053%2C1298938%2C1199007%2C489894%2C1230199%2C342178%2C1213079%2C1301444&optimus_uuid=D0EC4EA08F7311EA92D7A7093D0AD1C8AE82D8886EA7478AA5B7AB23C8A9C2AC&optimus_risk_level=71&optimus_code=10' : '/ajax/moreComingList?ci=65&token=&limit=10&movieIds=344450%2C346210%2C1216053%2C1298938%2C1199007%2C489894%2C1230199%2C342178%2C1213079%2C1301444&optimus_uuid=D0EC4EA08F7311EA92D7A7093D0AD1C8AE82D8886EA7478AA5B7AB23C8A9C2AC&optimus_risk_level=71&optimus_code=10').then(res => {
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
    color: #666;
    padding: 12px 15px;
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
        .filmScore {
          height: 22px;
          span {
            color: #ffb232;
          }
        }
        .filmactor {
          height: 22px;
        }
    }

  }
}
.line-ellipsis {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>