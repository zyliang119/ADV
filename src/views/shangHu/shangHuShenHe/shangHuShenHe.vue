<template>
  <page-header-wrapper :title="false">
    <a-card>
      <a-form :from="form" layout="inline">
        <!--  -->
        <a-row type="flex" justify="space-around">
          <a-col>
            <a-form-item label="姓名/手机号">
              <a-input />
            </a-form-item>
          </a-col>
          <a-col>
            <a-form-item label="提交时间">
              <a-range-picker
                :disabled-date="disabledDate"
                :disabled-time="disabledRangeTime"
                :show-time="{
                  hideDisabledOptions: true,
                  defaultValue: [moment('00:00:00', 'HH:mm:ss'), moment('11:59:59', 'HH:mm:ss')],
                }"
                format="YYYY-MM-DD HH:mm:ss"
              />
            </a-form-item>
          </a-col>
          <!--  -->
          <a-col>
            <a-form-item label="审核状态">
              <a-select default-value="lucy">
                <a-select-option value="jack">
                  Jack
                </a-select-option>
              </a-select>
            </a-form-item>
          </a-col>
          <!--  -->
          <a-col>
            <a-form-item>
              <a-row type="flex" justify="end" :gutter="12">
                <a-col><a-button type="primary">查询</a-button></a-col>
                <a-col><a-button>重置</a-button></a-col>
              </a-row>
            </a-form-item>
          </a-col>
        </a-row>
      </a-form>
      <a-table :columns="columns" :dataSource="dataSource" rowKey="id">
        <span slot="action" slot-scope="w">
          <!-- slot="action" 插槽名 -->
          <!-- slot-scope="record" // 该插槽内部能搞抓取到的改行的数据 -->
          <!-- 也可展示改行对应的内容 {{ record.name }} -->
          <a href="javascript:;" @click.stop="editHandle(w)">编辑</a>
          <a-divider type="vertical"/>
          <a href="javascript:;" @click.stop="deleteRecord(w)">删除</a>
        </span>
      </a-table>
    </a-card>
  </page-header-wrapper>
</template>
<script>
import moment from 'moment'
const columns = [
  {
    dataIndex: 'id',
    align: 'left',
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
    dataIndex: 'agent',
    title: '代理商'
  },
  {
    dataIndex: 'branch',
    title: '业务网点'
  },
  {
    dataIndex: 'applyTime',
    title: '申请时间'
  },
  {
    dataIndex: 'status',
    title: '审核状态'
  },
  {
    title: '操作',
    key: 'action',
    align: 'center',
    scopedSlots: { customRender: 'action' }
  }
]
const dataSource = [
  {
    id: '1',
    name: '刘才',
    position: '经理',
    agent: '信昌',
    branch: 'AA分公司',
    applyTime: '2020-09-10 15:12:01',
    status: '待审核'
  },
  {
    id: '2',
    name: '张三',
    position: '销售经理',
    agent: '利星',
    branch: 'QQ分公司',
    applyTime: '2020-11-10 08:35:25',
    status: '待审核'
  }
]
export default {
  data () {
      this.form = this.$form.createForm(this)
    return {
        columns: columns,
        dataSource: dataSource
    }
  },
  methods: {
    moment,
    range (start, end) {
      const result = []
      for (let i = start; i < end; i++) {
        result.push(i)
      }
      return result
    },
    disabledDate (current) {
      // Can not select days before today and today
      return current && current < moment().endOf('day')
    },

    disabledDateTime () {
      return {
        disabledHours: () => this.range(0, 24).splice(4, 20),
        disabledMinutes: () => this.range(30, 60),
        disabledSeconds: () => [55, 56]
      }
    },

    disabledRangeTime (_, type) {
      if (type === 'start') {
        return {
          disabledHours: () => this.range(0, 60).splice(4, 20),
          disabledMinutes: () => this.range(30, 60),
          disabledSeconds: () => [55, 56]
        }
      }
      return {
        disabledHours: () => this.range(0, 60).splice(20, 4),
        disabledMinutes: () => this.range(0, 31),
        disabledSeconds: () => [55, 56]
      }
    },
    editHandle (record) {
        console.log(record)
    },
    deleteRecord (record) {
        console.log(record.position)
    }
  }
}
</script>
<style scoped>
</style>
