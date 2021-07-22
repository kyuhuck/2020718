<template>
    <div>
        <h1>여기는tv세션입니다</h1>
        <div v-for="(user,i) in users" :key="i" >{{user.title}}</div>

        <button v-on:click="test">최상단상단 타이틀 불러오기</button><br>
        조회수:{{cnt}}<button v-on:click="test2">좋아요</button>
    </div>

</template>

<script>
    import axios from "axios";
    export default {

        data() {
            return{
                cnt : 0,
                users : [],
                name  : "kyuhuck",
                password:null
            }
        },
        watch :{
            cnt(){
            alert("증가이벤트가 발생하였습니다.");
            },
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

            },
            test2() {
                this.cnt++;

            },

        }


    };

</script>