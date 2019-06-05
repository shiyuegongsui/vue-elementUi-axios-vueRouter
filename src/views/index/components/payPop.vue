<template>
<el-dialog title="支付" width="600px" :append-to-body="true" :close-on-click-modal="false" :visible.sync="show">

    我是弹出层
</el-dialog>
</template>

<script>
export default {

    data() {
        return {
            show: false,
        }
    },
    methods: {}
}
</script>

<style lang="scss" scoped>
</style>
