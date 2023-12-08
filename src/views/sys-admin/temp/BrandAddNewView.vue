<template>
  <div>
    <h1>添加品牌</h1>
    <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
      <el-form-item label="名称" prop="name">
        <el-input v-model="ruleForm.name"></el-input>
      </el-form-item>
      <el-form-item label="拼音" prop="pinyin">
        <el-input v-model="ruleForm.pinyin"></el-input>
      </el-form-item>
      <el-form-item label="LOGO" prop="logo">
        <el-input v-model="ruleForm.logo"></el-input>
      </el-form-item>
      <el-form-item label="简介" prop="description">
        <el-input v-model="ruleForm.description"></el-input>
      </el-form-item>
      <el-form-item label="关键词" prop="keywords">
        <el-input v-model="ruleForm.keywords"></el-input>
      </el-form-item>
      <el-form-item label="排序序号" prop="sort">
        <el-input v-model="ruleForm.sort"></el-input>
      </el-form-item>
      <el-form-item label="是否启用" prop="enable">
        <el-switch
            v-model="ruleForm.enable"
            active-color="#13ce66"
            inactive-color="#ff4949"
            active-value="1"
            inactive-value="0">
        </el-switch>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submitForm('ruleForm')">添加品牌</el-button>
        <el-button @click="resetForm('ruleForm')">重置</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ruleForm: {
        name: '',
        description: '',
        sort: '',
        enable: '',
        keywords: '',
        logo: '',
        pinyin: ''
      },
      rules: {
        name: [
          {required: true, message: '请输入品牌名称', trigger: 'blur'},
          {min: 2, max: 20, message: '长度在 2 到 20 个字符', trigger: 'blur'}
        ],
        pinyin: [
          {required: true, message: '请输入品牌的拼音', trigger: 'blur'},
          {min: 4, max: 25, message: '长度在 4 到 25 个字符', trigger: 'blur'}
        ],
        description: [
          {required: true, message: '请输入品牌简介', trigger: 'blur'},
          {min: 2, max: 30, message: '长度在 2 到 30 个字符', trigger: 'blur'}
        ],
        sort: [
          {pattern: /^(\d{1}|[0-9]{1}[0-9]?)$/, message: '自定义排序序号必须是0-99之间的数字', trigger: 'blur'}

        ]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          // alert('您输入的用户名和密码的格式是正确的，但是，登录功能我们还没做!');
          let url = 'http://localhost:9090/brands/add-new';
          console.log('尝试添加相册')
          console.log('请求路径为:' + url)
          console.log('请求参数为:' + this.ruleForm)
          console.log(this.ruleForm)
          let fromDate = this.qs.stringify(this.ruleForm)
          console.log('将ruleForm转换为fromDate')
          console.log(fromDate)
          this.axios.post(url, fromDate).then((response) => {
            console.log(response);
            let responseDate = response.data
            if (responseDate.state == 20000) {
              console.log('添加品牌成功');
              this.$message({
                message: '添加品牌成功',
                type: 'success'
              });
            } else {
              console.log(responseDate.message)
              this.$notify.error({
                title: '添加品牌失败',
                message: responseDate.message
              });
            }
          });
        } else {
          console.log('error submit!!')
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
}
</script>

<style scoped>

</style>