<template>
  <!-- hidden PageHeaderWrapper title demo -->
  <page-header-wrapper :title="false" ><!--content="表单页用于向用户收集或验证信息，基础表单常见于数据项较少的表单场景。"-->
    <a-card :body-style="{padding: '24px 32px'}" :bordered="false">
      <a-form @submit="handleSubmit" :form="form">
        <a-row>
          <a-col :xs="4" :sm="4" :md="4" :lg="4" :xl="4">
            <a-form-item
              label="姓名"
              :labelCol="{lg: {span: 7}, sm: {span: 7}}"
              :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
              <a-input
                v-decorator="[
                  'name',
                  {rules: [{ required: true, message: '请输入标题' }]}
                ]"
                name="name"
                placeholder="请输入" />
            </a-form-item>
          </a-col>
          <a-col :xs="4" :sm="4" :md="4" :lg="4" :xl="4">
            <a-form-item
              label="代理商"
              :labelCol="{lg: {span: 7}, sm: {span: 7}}"
              :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
              <a-select defaultValue="alipay" style="width: 100px">
                <a-select-option value="alipay">--</a-select-option>
                <a-select-option value="wexinpay">1</a-select-option>
                <a-select-option value="wexinpay">2</a-select-option>
              </a-select>
            </a-form-item>
          </a-col>
          <a-col :xs="4" :sm="4" :md="4" :lg="4" :xl="4">
            <a-form-item
              label="充值状态"
              :labelCol="{lg: {span: 7}, sm: {span: 7}}"
              :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
              <a-select defaultValue="alipay" style="width: 100px">
                <a-select-option value="alipay">--</a-select-option>
                <a-select-option value="wexinpay">1</a-select-option>
                <a-select-option value="wexinpay">2</a-select-option>
              </a-select>
            </a-form-item>
          </a-col>
          <a-col :xs="6" :sm="6" :md="6" :lg="6" :xl="6">
            <a-form-item
              label="充值时间"
              :labelCol="{lg: {span: 7}, sm: {span: 7}}"
              :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
             <a-date-picker @change="onChange" />
            </a-form-item>
          </a-col>
          <a-col :xs="6" :sm="6" :md="6" :lg="6" :xl="6">
            <a-form-item
              label
              :labelCol="{lg: {span: 7}, sm: {span: 7}}"
              :wrapperCol="{lg: {span: 16}, sm: {span: 16} }" >
              <!-- <a-row type="flex" justify="end">
                <a-col>
                  <a-button type="primary" html-type="submit">
                    查询
                  </a-button>
                </a-col>
                <a-col>
                  <a-button html-type="submit">
                  重置
                  </a-button>
                </a-col>
              </a-row> -->
              <a-row type="flex" justify="end">
                <a-col >
                  <a-button type="primary" html-type="submit">
                    查询
                  </a-button>
                </a-col>
                <a-col :offset="1">
                  <a-button html-type="submit">
                  重置
                  </a-button>
                </a-col>
              </a-row>
            </a-form-item>
          </a-col>
        </a-row>

        <!-- <a-form-item
          label="目标描述"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
          <a-textarea
            rows="4"
            placeholder="请输入你阶段性工作目标"
            v-decorator="[
              'description',
              {rules: [{ required: true, message: '请输入目标描述' }]}
            ]" />
        </a-form-item> -->
        <!-- <a-form-item
          label="衡量标准"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
          <a-textarea
            rows="4"
            placeholder="请输入衡量标准"
            v-decorator="[
              'type',
              {rules: [{ required: true, message: '请输入衡量标准' }]}
            ]" />
        </a-form-item> -->
        <!-- <a-form-item
          label="客户"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
          <a-input
            placeholder="请描述你服务的客户，内部客户直接 @姓名／工号"
            v-decorator="[
              'customer',
              {rules: [{ required: true, message: '请描述你服务的客户' }]}
            ]" />
        </a-form-item> -->
        <!-- <a-form-item
          label="邀评人"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }"
          :required="false"
        >
          <a-input placeholder="请直接 @姓名／工号，最多可邀请 5 人" />
        </a-form-item> -->
        <!-- <a-form-item
          label="权重"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }"
          :required="false"
        >
          <a-input-number :min="0" :max="100" />
          <span> %</span>
        </a-form-item> -->
        <!-- <a-form-item
          label="目标公开"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }"
          :required="false"
          help="客户、邀评人默认被分享"
        >
          <a-radio-group v-decorator="['target', { initialValue: 1 }]">
            <a-radio :value="1">公开</a-radio>
            <a-radio :value="2">部分公开</a-radio>
            <a-radio :value="3">不公开</a-radio>
          </a-radio-group>
          <a-form-item v-show="form.getFieldValue('target') === 2">
            <a-select mode="multiple">
              <a-select-option value="4">同事一</a-select-option>
              <a-select-option value="5">同事二</a-select-option>
              <a-select-option value="6">同事三</a-select-option>
            </a-select>
          </a-form-item>
        </a-form-item> -->
        <a-form-item
          :wrapperCol="{ span: 24 }"
          style="text-align: center"
        >
          <a-button htmlType="submit" type="primary">提交</a-button>
          <a-button style="margin-left: 8px">保存</a-button>
        </a-form-item>
      </a-form>

    </a-card>
  </page-header-wrapper>
</template>

<script>
export default {
  name: 'BaseForm',
  data () {
    return {
      form: this.$form.createForm(this)
    }
  },
  methods: {
    // handler
    handleSubmit (e) {
      e.preventDefault()
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values)
        }
      })
    },
    onChange (e) {

    }
  }
}
</script>
