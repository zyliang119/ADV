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
        <a-form-item
          :wrapperCol="{ span: 24 }"
          style="text-align: center"
        >

        </a-form-item>
      </a-form>
    <s-table
        style="margin-bottom: 24px"
        row-key="id"
        :columns="goodsColumns"
        :data="loadData">

      </s-table>
    </a-card>
  </page-header-wrapper>
</template>

<script>

import { STable } from '@/components'
import { getServiceList } from '@/api/manage'
export default {
  name: 'BaseForm',
  components: {
    STable
  },
  data () {
    return {
      form: this.$form.createForm(this),
      goodsColumns: [
        {
          title: '序号',
          dataIndex: 'id',
          key: 'id'
        },
        {
          title: '用户名字',
          dataIndex: 'name',
          key: 'name'
        },
        {
          title: '询价品类',
          dataIndex: 'barcode',
          key: 'barcode'
        },
        {
          title: '产品名称',
          dataIndex: 'price',
          key: 'price',
          align: 'right'
        },
        {
          title: '线索等级',
          dataIndex: 'num',
          key: 'num',
          align: 'right'
        },
        {
          title: '网点',
          dataIndex: 'amount',
          key: 'amount',
          align: 'right'
        },
        {
          title: '询价时间',
          dataIndex: 'num',
          key: 'num',
          align: 'right'
        },
        {
          title: '产品消费率',
          dataIndex: 'num',
          key: 'num',
          align: 'right'
        },
        {
          title: '更新时间',
          dataIndex: 'num',
          key: 'num',
          align: 'right'
        },
        {
          title: '操作',
          dataIndex: 'num',
          key: 'num',
          align: 'right'
        }
      ],
      // 加载数据方法 必须为 Promise 对象
      loadData: parameter => {
        console.log('loadData.parameter', parameter)
        return getServiceList(Object.assign(parameter, this.queryParam))
          .then(res => {
            return res.result
          })
      }
      // 加载数据方法 必须为 Promise 对象
      // loadGoodsData: () => {
      //   return new Promise(resolve => {
      //     resolve({
      //       data: [
      //         {
      //           id: '1234561',
      //           name: '矿泉水 550ml',
      //           barcode: '12421432143214321',
      //           price: '2.00',
      //           num: '1',
      //           amount: '2.00'
      //         },
      //         {
      //           id: '1234562',
      //           name: '凉茶 300ml',
      //           barcode: '12421432143214322',
      //           price: '3.00',
      //           num: '2',
      //           amount: '6.00'
      //         },
      //         {
      //           id: '1234563',
      //           name: '好吃的薯片',
      //           barcode: '12421432143214323',
      //           price: '7.00',
      //           num: '4',
      //           amount: '28.00'
      //         },
      //         {
      //           id: '1234564',
      //           name: '特别好吃的蛋卷',
      //           barcode: '12421432143214324',
      //           price: '8.50',
      //           num: '3',
      //           amount: '25.50'
      //         }
      //       ],
      //       pageSize: 10,
      //       pageNo: 1,
      //       totalPage: 1,
      //       totalCount: 10
      //     })
      //   }).then(res => {
      //     return res
      //   })
      // }
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
