<template>
    <div>
        <h1>여기는tv세션입니다</h1>
        <div v-for="(user,i) in users" :key="i" >{{user.title}}</div>

        <button v-on:click="test">최상단상단 타이틀 불러오기</button>
    </div>

</template>

<script>
    import axios from "axios";
    export default {

        data() {
            return{
                email : null,
                users : [],
                name  : "kyuhuck",
                password:null
            }
        },
        methods: {
            test() {
                var vm  = this;
                axios
                    .get("http://static.cloud.sbs.co.kr/2021main/top/index.json")
                    .then(res =>{
                        // handle success
                        console.log(res);
                        vm.users = res.data;


                    })
                    .catch(err => {
                        // handle error
                        console.log(err);
                    })
                    .then(() => {
                        // always executed
                    });

            }
        }


    };

</script>