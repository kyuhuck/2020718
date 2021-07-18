<template>

    <div>
        <h2>여기는sbs홈</h2>


        <b-container fluid class="p-4 bg-dark">
            <b-row>
                <b-col v-for="(user,i) in users" :key="i" >
                    <b-img thumbnail fluid  :src="user.pgm_img_url" alt="Image 1"></b-img>
                </b-col>



            </b-row>
        </b-container>
    </div>

</template>


<script>
    import axios from "axios";
    export default {
        mounted() {
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