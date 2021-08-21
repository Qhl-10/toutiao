<template>
    <el-card>
        <Breadcrumbs></Breadcrumbs>
        <el-table :data="list">
          <el-table-column prop="id" label="序号"></el-table-column>
          <el-table-column width="600" prop="name" label="标题"></el-table-column>
          <el-table-column prop="status" label="评论状态"></el-table-column>
          <el-table-column prop="allnumber" label="总评论数"></el-table-column>
          <el-table-column prop="fannumber" label="粉丝评论数"></el-table-column>
          <el-table-column label="操作">
            <template slot-scope="scope" class="active">
              <el-button @click="editDtata(scope.row)" type="primary" icon="ei-icon-edit" circle></el-button>
              <el-button @click="removeData(scope.row.id)" type="danger"></el-button>
            </template>
          </el-table-column>
        </el-table>
        <el-row :gutter="20">
          <el-col :span="6" :offset="12">
            <div class="block">
              <el-pagination :total="total" :current-page.sync="currentPage" :page-size="pageSize" @current-change="handleCurrentChang" layout="total, prev, next, jumper, pager"></el-pagination>
            </div>
          </el-col>
        </el-row>
    </el-card>
</template>
<script>
import Breadcrumbs from '../../components/common/bread-crumb.vue'
export default {
  components: {
    Breadcrumbs
  },
  data () {
    return {
      currentPage: 1,
      pageSize: 8,
      tableData: []
    }
  },
  methods: {
    getComment () {
      this.$axios({
        url: 'http://127.0.0.1:5000/home/comment',
        params: {
          response_type: 'comment'
        }
      }).then(res => {
        console.log(res)
      })
    }
  },
  created () {
    this.getComment()
  }
}
</script>
