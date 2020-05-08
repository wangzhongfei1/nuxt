<template>
    <div>
        {{filmInfo.name}}
        <img :src="filmInfo.poster" alt="">
    </div>
    
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            filmInfo: null
        }
    },
    layout: 'detailTemplate',
    asyncData(data) {
        return axios({
             url: `https://m.maizuo.com/gateway?filmId=4487&k=9977826`,
             headers: {
                'X-Client-Info': '{"a":"3000","ch":"1002","v":"5.0.4","e":"15886737532641404887998","bc":"110100"}',
                 'X-Host': 'mall.film-ticket.film.info'
            }
        }).then(res => {
            return {
                filmInfo: res.data.data.film
            }
        })
    }
}
</script>