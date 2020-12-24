<template>
  <page-header-wrapper :title="false">
    <a-form :form="form" :label-col="{ span:2 }" :wrapper-col="{ span: 4 }">
      <a-card title="方案信息" class="card-padding">
        <a-form-item label="方案名称">
          <a-input
          placeholder="请填写"
          v-decorator="[
          'fangAnMingCheng',
          {
            initialValue: fangAnMingCheng,
            rules: [{ required: true ,message: '方案名称不能为空'}]
            }]"/>
        </a-form-item>
        <a-form-item label="适用品类">
          <a-select default-value="--" @change="handleChange">
            <a-select-option value="挖掘机">挖掘机</a-select-option>
          </a-select>
        </a-form-item>
        <a-form-item label="备注">
            <a-input v-decorator="[ 'beiZhu' ]" placeholder="请填写" />
        </a-form-item>
      </a-card>
      <a-card title="定价信息-履带式" class="card-padding">
        <a-table :columns="columns"></a-table>
      </a-card>
      <a-card title="定价信息-轮式" class="card-padding">
        <a-table :columns="columns"></a-table>
          <a-row type="flex" :gutter="24" justify="center" style="margin-top: 30px;">
           <a-col><a-button type="primary">确定</a-button></a-col>
           <a-col><a-button @click="$router.back(-1)">取消</a-button></a-col>
          </a-row>
      </a-card>
    </a-form>
  </page-header-wrapper>
</template>
<script>
const columns = [
    {
        title: '级别',
        dataIndex: ''
    },
    {
        title: 'A+级线索（元/条）',
        dataIndex: ''
    },
    {
        title: 'A级线索（元/条）',
        dataIndex: ''
    },
    {
        title: 'B级线索（元/条）',
        dataIndex: ''
    },
    {
        title: '备注',
        dataIndex: ''
    },
    {
        title: '操作',
        dataIndex: ''
    }
]

export default {
  data () {
    this.form = this.$form.createForm(this)
    return {
      fangAnMingCheng: '123',
      beiZhu: '',
      columns: columns
    }
  },
  methods: {
    handleChange (val) {
      console.log(val)
    }
  }
}
</script>
<style>
.card-padding{
    margin-bottom: 30px;
}
</style>
