<template>
  <div>
    <div slot="header">
      <el-row>
        <el-col style="text-align: left" :span="12">人文讲座</el-col>
        <el-col :span="6">已参与的讲座：{{ num }}</el-col>
        <el-col :span="6">已获得的学时：{{ hour }}</el-col>
      </el-row>
    </div>
    <el-collapse v-model="activeNames" @change="handleChange">
      <el-collapse-item title="最新" name="new">
        <el-table :data="tableNew" stripe style="width: 100%">
          <el-table-column prop="name" label="讲座名称"> </el-table-column>
          <el-table-column prop="hour" label="学时"> </el-table-column>
          <el-table-column prop="time" label="时间"> </el-table-column>
          <el-table-column fixed="right" label="报名" width="100">
            <template slot-scope="scope">
              <el-button
                @click="handleClick(scope.row)"
                type="text"
                size="small"
                >报名</el-button
              >
            </template>
          </el-table-column>
        </el-table>
      </el-collapse-item>
      <el-collapse-item title="全部" name="all">
        <el-table :data="tableAll" stripe style="width: 100%">
          <el-table-column prop="name" label="讲座名称"> </el-table-column>
          <el-table-column prop="hour" label="学时"> </el-table-column>
          <el-table-column prop="time" label="时间"> </el-table-column>
          <el-table-column fixed="right" label="报名" width="100">
            <template slot-scope="scope">
              <el-button
                @click="handleClick(scope.row)"
                type="text"
                size="small"
                >报名</el-button
              >
            </template>
          </el-table-column>
        </el-table>
      </el-collapse-item>
    </el-collapse>
  </div>
</template>

<script>
export default {
  methods: {
    handleClick (row) {
      console.log(row)
    },
    handleChange (val) {
      console.log(val)
    }
  },
  data () {
    return {
      hour: '2',
      num: '1',
      activeNames: ['new', 'all'],
      tableNew: [
        {
          name: '现代地球-生命系统的形成',
          hour: '2',
          time: '2020-12-23 19:00-20:50',
        },
      ],
      tableAll: [
        {
          name: '现代地球-生命系统的形成',
          hour: '2',
          time: '2020-12-23 19:00-20:50',
        },
        {
          name: '东北老工业基地城镇化与城市发展',
          hour: '2',
          time: '2020-12-19 19:00-21:00',
        },
        {
          name: '青藏高原隆升与环境效应',
          hour: '2',
          time: '2020-12-16 19:00-20:50',
        },
      ],
    }
  },
}
</script>
