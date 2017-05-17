<template>
    <div id="home_page">
        <div class="investTop">
            <h3>
                <span>预计可免费赚取</span>
                <span class="u-num">{{Interest}}</span>
                <span class="u-unit">元</span>
            </h3>
            <div class="experience">
                <div class="experienceL">
    
                </div>
                <div class="experienceR">
                    <p class="exText">体验金
                        <i></i>
                    </p>
                    <p class="exNum">18,888.00
                        <span>元</span>
                    </p>
                </div>
            </div>
            <div class="freeget">
                <div class="btn" @click="freeGetBtn">免费领取 </div>
            </div>
        </div>
        <div class="investBot">
            <div class="sign" @click="sign">
                <div class="sign_circle">
                    <div class="sign_circle_top">
                        <i></i>
                        <span class="circle_text">加息</span>
                    </div>
                    <p>
                        <strong>5</strong>.8%</p>
                </div>
                <div class="sign_text">签到</div>
            </div>
            <div class="income">
                <router-link :to="{name:'product-detail',params:{id:productId}}">
                    <div class="mortgage">
                        <i class="mortgageIcon"></i>{{ProductName}}</div>
                    <h3>预期年化收益</h3>
                    <p class="incomeNum">
                        <b>{{InterestRate}}</b>%</p>
                    <div class="loan">
                        <div class="loanLeft">
                            <p class="pNum">
                                <span>{{Term}}</span>{{UnitText}}</p>
                            <p class="pText">项目期限</p>
                        </div>
                        <div class="loanRight">
                            <p class="pNum">
                                <span>{{Amount}}</span>元</p>
                            <p class="pText">借款金额</p>
                        </div>
                    </div>
                    <div class="progress">
                        <p class="pText">
                            <span class="progress_text">投资进度</span>
                            <span class="progress_num">{{progress}}</span>
                        </p>
                        <div class="progress_bar_outer">
                            <div class="progress_bar_inner"></div>
                        </div>
                    </div>
                </router-link>
                <router-link class="Invitation" :to="{name:'product-detail',params:{id:productId}}">立即投资</router-link>
            </div>
            <div class="more">
                <router-link to="/invest">
                    <span>更多产品</span>
                    <i></i>
                </router-link>
            </div>
        </div>
        <alert-tip v-if="showAlert" :showHide="showAlert" @closeTip="closeTip" :alertText="alertText"></alert-tip>
        <div :class="{alertTipCls:showAlert}"></div>
    </div>
</template>
<script>
export default {
    data: function () {
        return {
            productId: null,
            experienceId: null,
            freeGetNumber: 0,
            ProductName: null, //产品名称
            InterestRate: null, //年化收益率
            Amount: null, //借款金额
            Term: null, //项目期限
            showAlert: false, //显示弹窗组件
            alertText: null, //弹窗内容
            UnitText: null, //项目期限单位
            Interest: null,
            href: null,
            progress: null //进度
        }
    },
    created: function () {
        this.getHomeData();
        this.href = window.location.href;
        this.$nextTick(function () {
            this.getExperienceData();
            this.getHomeData();
        });


    },
    methods: {
        // getHomeData() {
        //     apicall.call('Product', 'Home', null, { MemberId: '', appkey: 'yp3Ify2d4PZU33MSdio5ITT4DiHFy59g', appSecret: 'oAyHBnoWGvualtbJgC0v5QMwwKLk9G0B' }).then(function (res) {
        //         console.log(2);
        //     })
        // }
        getHomeData:function(params) {
            var v = this;
            v.$api.post('Product/Home', params, function (r) {
                console.log(r.data);
            })
        }

    }
}
</script>
