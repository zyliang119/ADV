<template>
  <page-header-wrapper :title="false" >
    <a-card :body-style="{padding: '24px 32px'}" :bordered="false">
      <a-form :form="form" class="form" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }" @submit="handleSubmit">
        <a-row class="form-row" :gutter="[24,16]">
          <a-col :lg="4" :sm="24">
            <a-form-item>
              <router-link to="./tuanJiaDingJia">
                <a-button type="primary">
                  <a-icon type="plus" /> 添加定价方案
                </a-button>
              </router-link>
            </a-form-item>
          </a-col>
          <a-col :lg="4" :sm="24">
            <a-form-item
             label="品类:"
             >
              <a-select>
                <a-select-option value="1">1</a-select-option>
                <a-select-option value="2">2</a-select-option>
              </a-select>
            </a-form-item>
          </a-col>
          <a-col :lg="8" :sm="24">
            <a-form-item label="仓库名">
              <a-input
                  placeholder="请输入仓库名称"
                  v-decorator="[
                  'name',
                  {rules: [{ required: true, message: '请输入仓库名称', whitespace: true}]}
                  ]" />
            </a-form-item>
          </a-col>
          <a-col :lg="8" :sm="24" :style="{ textAlign: 'right' }">
            <a-button type="primary" :style="{ marginRight:'8px'}">查&nbsp;询</a-button>
            <a-button :style="{ marginRight:'12px'}">重&nbsp;置</a-button>
          </a-col>
        </a-row>
      </a-form>
      <a-table :columns="columns" :data-source="tableData">
      </a-table>
    </a-card>
  </page-header-wrapper>
</template>
<script>
const columns = [
  {
    title: '序号',
    dataIndex: 'indexNo',
    align: 'left',
    slots: { title: 'ii' }
  },
  {
    title: '方案名称',
    dataIndex: 'case'
  },
  {
    title: '适用品类',
    dataIndex: 'cate'
  },
  {
    title: '机型',
    dataIndex: 'model'
  },
  {
    title: '备注',
    dataIndex: 'remark'
  },
  {
    title: '状态',
    dataIndex: 'status'
  },
  {
    title: '更新时间',
    dataIndex: 'updateTime'
  },
  {
    title: '操作',
    dataIndex: ''
  }
]
const tableData = []
export default {
  name: 'XianSuoDingJia',
  data () {
    return {
      columns,
      tableData
    }
  },
  methods: {
    // handler
    handleSubmit (e) {
      console.log(e)
      e.preventDefault()
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values)
        }
      })
    }
  }
}
</script>

<style scoped>

</style>
