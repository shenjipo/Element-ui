<template>
    <el-dialog title="提示" :visible.sync="dialogVisible" width="30%">
        <el-table :data="gridData">
            <el-table-column property="date" label="日期" width="150"></el-table-column>
            <el-table-column property="name" label="姓名" width="200"></el-table-column>
            <el-table-column property="address" label="地址"></el-table-column>
        </el-table>
        <span slot="footer" class="dialog-footer">
            <el-button @click="handleCancel">取 消</el-button>
            <el-button type="primary" @click="handleConfirm">确 定</el-button>
        </span>
    </el-dialog>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';
@Component({
    components: {

    },
})
export default class SettingDialog extends Vue {
    dialogVisible: boolean = true
    gridData: Array<any> = [{
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
    }, {
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
    }, {
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
    }, {
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
    }]
    @Prop() data: any
    @Prop() onConfirm: any
    handleCancel() {
        this.$emit('hide')
    }

    handleConfirm() {
        console.log('从父组件接收的参数', this.data)
        this.onConfirm(this.gridData)
       
    }
}
</script>
<style lang="scss" scoped>
.el-select {
    width: 150px;
}
</style>
<style lang="scss"></style>
