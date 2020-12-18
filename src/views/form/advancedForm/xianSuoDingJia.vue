<template>
  <page-header-wrapper :title="false" >
    <a-card :body-style="{padding: '24px 32px'}" :bordered="false">
      <a-form :form="form" class="form" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }" @submit="handleSubmit">
        <a-row class="form-row" :gutter="[24,16]">
          <a-col :lg="4" :sm="24">
              <a-form-item>
                <a-button type="primary">
                  <a-icon type="plus" /> 添加定价方案
                </a-button>
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
          <a-col :lg="8" :sm="24">
            <a-form-item>
              <a-space>
                <a-button type="primary">查&nbsp;询</a-button>
                <a-button>重&nbsp;置</a-button>
              </a-space>
            </a-form-item>
          </a-col>
        </a-row>
      </a-form>
    </a-card>
  </page-header-wrapper>
</template>
<script>
export default {
  name: 'XianSuoDingJia',
  data () {
    return {}
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
  .bgColor{background-Color:pink;}
</style>
