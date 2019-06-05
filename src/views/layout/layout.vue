<template>
<div id="app">
    <div class="bg">

    </div>
    <img src="~@/assets/images/header-logo.png">
    <router-view></router-view>
    <dz-footer></dz-footer>
</div>
</template>

<script>
import dzFooter from '@/components/common/dzFooter';
import {
    validate
} from "@/plugins/validate.js";

export default {
    name: 'layOut',
    components: {
        dzFooter
    },
    data() {
        return {
            loading: false,
            finished: false,
            totalCount: 0,
            list: [],
            query: {
                pageIndex: 1,
                pageSize: 10
            },
        }
    },
    created() {
        console.log(validate);
    },
    methods: {
        getDetail() {
            this.$ajax.get("/index/countWare", {
                params: {}
            }).then(res => {});
        },
        getList() {
            var that = this;
            that.loading = true;
            that.finished = false;
            this.$ajax.post("/record/listDetectionRecord", {
                pageIndex: that.query.pageIndex,
                pageSize: that.query.pageSize
            }).then(res => {
                that.finished = true;
                that.loading = false;
                that.list = res.result.list;
                that.totalCount = res.result.totalCount;
            });
        },
    }
}
</script>

<style lang="scss" scoped>
.bg {
    width: 120px;
    height: 63px;
    background: url("~@/assets/images/header-logo.png") center no-repeat;
    background-size: cover;

}
</style>
