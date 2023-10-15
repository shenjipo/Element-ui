<template>
    <div>
        <el-select v-model="value" placeholder="请选择" popper-class="custom-select">
            <el-option-group v-for="group in options" :key="group.label" >
                <el-option v-for="item in group.options" :key="item.value" :label="item.label" :value="item.value">
                </el-option>
            </el-option-group>
        </el-select>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
@Component({
    components: {

    },
})
export default class Select extends Vue {
    options: any = [
        {
            label: 'aaa',
            options: [{
                value: 'Chengdu',
                label: '成都'
            }, {
                value: 'Shenzhen',
                label: '深圳'
            }, {
                value: 'Guangzhou',
                label: '广州'
            }, {
                value: 'Dalian',
                label: '大连'
            }, {
                value: '2',
                label: '大连1'
            }, {
                value: '3',
                label: '大连2'
            }, {
                value: '4',
                label: '大连3'
            }]
        },
        {
            label: 'bbb',
            options: [{
                value: 'manage',
                label: '仪表盘管理'
            }, {
                value: 'create',
                label: '新建仪表盘'
            }]
        }
    ]
    value: string = 'Guangzhou'

}
</script>
<style lang="scss" scoped>
.el-select {
    width: 150px;
}
</style>
<style lang="scss">
.custom-select {
    .el-select-dropdown__list {
        .el-select-group__wrap:first-child {
            max-height: 150px;
            overflow-y: auto;
            overflow-x: hidden;
            padding-bottom: 0;

        }
        .el-select-group__wrap:first-child::after {
            display: none;
        }
        .el-select-group__wrap:last-child::before {
            content: '';
            position: absolute;
            display: block;
            left: 20px;
            right: 20px;
            top: 2px;
            height: 1px;
            background-color: #e4e7ed;
        }
    }
}
</style>
