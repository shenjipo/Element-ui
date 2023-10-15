<template>
    <div>
        <el-select v-model="value" placeholder="请选择" popper-class="remote-select" multiple filterable
            :filter-method="handleRemote" :loading="repoLoading" style="width: 400px;">

            <el-option v-for="item in repoOptions" :key="item.key" :label="item.label" :value="item.value">
            </el-option>

        </el-select>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
@Component({
    components: {

    },
})
export default class RemoteSelect extends Vue {
    repoOptions: Array<{ key: string, value: string, label: string }> = [

    ]
    repoLoading: boolean = false
    value: string = ''
    timer: any = null
    handleRemote(query: string) {
        if (query !== '') {
            this.repoLoading = true
            this.timer && clearTimeout(this.timer)

            this.timer = setTimeout(() => {
                this.mockApi().then((res: any) => {
                    this.repoOptions = res.data.map((item: any) => {
                        return {
                            value: item.value,
                            label: `${item.value}(${item.key})`,
                            key: item.key
                        }
                    })
                    this.repoLoading = false
                }).catch(err => {
                    this.repoLoading = false
                })
            }, 500)
        }
    }

    mockApi() {
        return new Promise((resolve, reject) => {
            setTimeout(() => {
                resolve({
                    code: 200,
                    msg: 'success',
                    data: [
                        { value: 'zfBpogjZP4sW9GzT0Wl8JEZbxsktD3C8', key: 'a' },
                        { value: '2hOTZzwxSWtpdodsyZQRb8APJGPhgHqO', key: 'b' },
                        { value: 'pcM03bmLQx5yOF0akfdf5kWUNPJiOOKg', key: 'c' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'd' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'e' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'f' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'g' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'h' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'i' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'j' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'k' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'l' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'm' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'n' },
                        { value: 'pHVHJ7COWTW8EvRg6zuzfrQwNBFOqXGP', key: 'o' },
                    ]
                })
            }, 400)
        })
    }
}
</script>
<style lang="scss" scoped>
.el-select {
    width: 150px;
}
</style>
<style lang="scss"></style>
