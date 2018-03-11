<template>
    <div id="app123">
        <h1>服务端数据为：{{serverData}}</h1>
        <img src="../../assets/logo.png" v-on:click="getData">
        <router-view></router-view>
    </div>
</template>

<script>
    export default {
        name: 'app123',
        data () {
            return {
                serverData: 'data from fake server'
            }
        },
        mounted: function () {
            this.getData()
        },
        methods: {
            getData () {
                console.log('-------getData')
                var that = this
                    //.$http.get('http://localhost:8080/BidAnalysis/hello/getUser/1')
                //192.168.1.101为后端IP地址     this.$http.get('http://192.168.1.101:8080/hello/getperson/33333')
                    .then(function (response) {
                        console.log(response)
                        console.log(this)
                        that.serverData = response.data
                    })
                    .catch(function (error) {
                        console.log(error)
                    })
            }
        }
    }
</script>