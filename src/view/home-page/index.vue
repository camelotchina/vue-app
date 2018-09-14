<template>
    <div class="hello">
       
        <header class="header">
            <h1>{{ msg }}</h1>
        </header>
        <h5 class="text_c">vuex</h5>

        <div class="box">
            <button type="primary" @click="reduceCont">-</button>
            <p>{{ getCont}}</p>
            <button type="primary" @click="addCont">+</button>
        </div>

        <div class="text_c">
            <p v-for="(item,index) in getList" :key="index">{{ item.a }}</p>
            <p>数量：{{ getListLength }}</p>
        </div>
         <p class="text_c">国际化：{{ $t('header.a') }}</p>
         <div class="text_c">
              <button type="primary" @click="setZh">zh-CN</button>
              <button type="primary" @click="setEn">en-US</button>
         </div>
    </div>
</template>

<script>
    import {
        mapActions,
        mapGetters
    } from "vuex";
    import imgLogo from "@/assets/img/logo.png";
    import Cookies from 'js-cookie'

    export default {
        name: "HelloWorld",
        data() {
            return {
                msg: "Welcome to Your Vue.js App"
            };
        },
        computed: {
            getCont() {
                return this.$store.state.cont.cont;
            },
            ...mapGetters(["getList", "getListLength"])
        },
        created(){
            
        },
        mounted(){
            
        },
        methods: {
            ...mapActions(["addCont", "reduceCont"]),
            setZh(){
                Cookies.set('lang','zh-CN');
                window.location.reload();
            },
            setEn(){
                Cookies.set('lang','en-US');
                window.location.reload();
            }
        }
    };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang='less'>
.header {
    text-align: center;
    padding: 20px 0;
}

.box {
    display: flex;
    align-items: center;
    justify-content: center;
    p {
        width: 120px;
        text-align: center;
    }
}

</style>
