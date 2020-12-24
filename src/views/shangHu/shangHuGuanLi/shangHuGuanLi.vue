<template>
  <page-header-wrapper :title="false">
    <a-card>
      <a-form :form="form" layout="inline">
        <a-row type="flex" justify="space-around">
          <a-col :lg=3>
            <a-form-item>
              <a-button type="primary"><a-icon type="plus" />开通适用</a-button>
            </a-form-item>
          </a-col>
          <a-col >
            <a-form-item label="姓名">
              <a-input v-decorator="[ 'userName' ]" placeholder="请输入"/>
            </a-form-item>
          </a-col>
          <a-col >
            <a-form-item label="代理品牌">
              <a-input v-decorator="[ 'agentBrand' ]" placeholder="请输入"/>
            </a-form-item>
          </a-col>
          <a-col >
            <a-form-item label="代理商">
              <a-select default-value="--">
                <a-select-option value="oo">利星</a-select-option>
              </a-select>
            </a-form-item>
          </a-col>
          <a-col >
            <a-form-item label="商户属性">
              <a-select default-value="--">
                <a-select-option value="00">正式</a-select-option>
              </a-select>
            </a-form-item>
          </a-col>
          <a-col>
            <a-row type="flex" justify="end" :gutter="12">
              <a-col><a-button type="primary">查询</a-button> </a-col>
              <a-col><a-button>重置</a-button></a-col>
            </a-row>
          </a-col>
        </a-row>
      </a-form>
      <a-table :columns="columns" :dataSource="dataSource" rowKey="id">
        <span slot="action" slot-scope="re">
          <a href="javascript:void(0)" @click="handleCheck(re)">查看</a>
        </span>
      </a-table>
    </a-card>
  </page-header-wrapper>
</template>
<script>
const columns = [
  {
    dataIndex: 'id',
    title: '序号'
  },
  {
    dataIndex: 'name',
    title: '姓名'
  },
  {
    dataIndex: 'position',
    title: '职务'
  },
  {
    dataIndex: 'agentBrand',
    title: '代理品牌'
  },
  {
    dataIndex: 'agent',
    title: '代理商'
  },
  {
    dataIndex: 'agentCate',
    title: '代理品类'
  },
  {
    dataIndex: 'businessSite',
    title: '业务网点'
  },
  {
    dataIndex: 'money',
    title: '账户金额(元)'
  },
  {
    dataIndex: 'gotClue',
    title: '已获取线索量(条)'
  },
  {
    dataIndex: 'lastLogin',
    title: '最后登录时间'
  },
  {
    dataIndex: 'action',
    title: '操作',
    key: 'action',
    scopedSlots: { customRender: 'action' }
  }
]
const dataSource = [
  {
    id: '1',
    name: 'Peter',
    position: '经理',
    agentBrand: '卡特',
    agent: '利星行',
    agentCate: '挖掘机',
    businessSite: '3',
    money: '1321',
    gotClue: '89',
    lastLogin: '2020-11-21 18:21:09'
  }
]
export default {
    data () {
      this.form = this.$form.createForm(this)
        return {
          columns: columns,
          dataSource: dataSource,
          userName: '',
          agentBrand: '',
          agent: ''
        }
    },
    methods: {
      handleCheck (re) {
        console.log(re)
      }
    }
}
</script>
<style scoped>

</style>
