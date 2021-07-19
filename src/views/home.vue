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
<!--        <ul>-->
<!--        <li v-for="(user,i) in users" :key="i" ><img :src="user.pgm_img_url" width="100" height="100"></li>-->


<!--        </ul>-->

        <slick ref="slick" :options="slickOptions">
            <div  v-for="(user,i) in users" :key="i" >  <img :src="user.pgm_img_url" ></div>



        </slick>

    </div>



</template>


<script>
    import axios from "axios";
    import Slick from 'vue-slick';
    //import VueSlickCarousel from 'vue-slick-carousel'
    import 'vue-slick-carousel/dist/vue-slick-carousel.css'
    // optional style for arrows & dots
    import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'
    import 'slick-carousel/slick/slick.css';
    export default {

        name: 'MyComponent',
        components: {Slick },



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
        beforeUpdate() {
            if (this.$refs.slick) {
                this.$refs.slick.destroy();
            }
        },
        updated() {
            this.$nextTick(function () {
                if (this.$refs.slick) {
                    this.$refs.slick.create(this.slickOptions);
                }
            });
        },
        data() {
            return{
                email : null,
                users : [],
                name  : "kyuhuck",
                password:null,
                slickOptions: {
                    //options can be used from the plugin documentation
                    slidesToShow: 1,
                    infinite: true,
                    accessibility: true,
                    adaptiveHeight: false,
                    arrows: true,
                    dots: true,
                    draggable: true,
                    edgeFriction: 0.30,
                    swipe: true

                }
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