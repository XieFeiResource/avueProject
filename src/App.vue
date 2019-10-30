<template>
  <el-row :gutter="20">
    <el-col :span="20" :offset="2">
      <div class="grid-content bg-purple">
        <avue-crud
          :data="data"
          :option="option"
          :page="page"
          @size-change="sizeChange"
          @current-change="currentChange"
        ></avue-crud>
        <br>
    </div>
    </el-col>
  </el-row>
</template>

<script>
  export default {
    data() {
      return {
        page: {
          pageSizes: [1, 5, 10, 15],
          currentPage: 1,
          total: 0,
          pageSize: 2
        },
        data: [
          {
            name: '张三',
            sex: '男'
          },
          {
            name: '李四',
            sex: '女'
          }
        ],
        option: {
          align: 'center',
          menuAlign: 'center',
          column: [
            {
              label: '姓名',
              prop: 'name'
            },
            {
              label: '性别',
              prop: 'sex'
            }
          ]
        }
      }
    },
    created() {
      this.getList()
    },
    methods: {
      getList() {
        this.page.total = 10
        if (this.page.currentPage === 1) {
          this.data = [
            {
              name: '张三',
              sex: '男'
            }
          ]
        } else if (this.page.currentPage == 2) {
          this.data = [
            {
              name: '李四',
              sex: '女'
            }
          ]
        }
      },
      sizeChange(val) {
        this.page.currentPage = 1
        this.page.pageSize = val
        this.getList()
        this.$message.success('行数' + val)
      },
      currentChange(val) {
        this.page.currentPage = val
        this.getList()
        this.$message.success('页码' + val)
      }
    }
  }
</script>

<style>
  .el-row {
    margin-bottom: 20px;
  }
  el-row:last-child {
     margin-bottom: 0;
   }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
</style>
