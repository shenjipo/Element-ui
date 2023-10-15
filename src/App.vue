<template>
  <div id="app">
    <Select></Select>
    <RemoteSelect></RemoteSelect>
    <Cascader></Cascader>
    <el-button @click="handleClick">打开dialog</el-button>
    <el-button @click="handTest">测试</el-button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Select from './views/Select.vue';
import RemoteSelect from './views/RemoteSelect.vue'
import Cascader from './views/Cascader.vue';
import SettingDialog from './views/SettingDialog.vue';
import JsDialog from './components/JsDialog';
@Component({
  components: {
    Select, RemoteSelect, Cascader
  },
})
export default class App extends Vue {
  data: any = {
    value: '213',
    key: 'fas',
  }

  handleClick() {
    // 第一个参数是要打开的弹窗组件，第二个参数是要传递给该组件的参数
    JsDialog(SettingDialog, {
      data: this.data,
      onConfirm: (data: any) => {
        console.log('从dialog接收的参数', data)

      }
    }).show()

  }
  created() {

  }
  handTest() {
    this.$emit('mytest')
  }
}
</script>
<style lang="scss"></style>
