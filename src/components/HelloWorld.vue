<template>
  <div>
    <!-- 显示数据库内容 -->
    <el-container  style="height: 500px; border: 1px solid #eee">
      <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
        <el-menu :default-openeds="['1', '3']">
          <el-submenu index="1">
            <template slot="title"><i class="el-icon-message"></i>用户</template>
            <el-menu-item-group>
              <template slot="title">用户数据</template>
              <el-menu-item data-index="1-1"  @click="main='admin'">用户管理</el-menu-item>
              <el-menu-item data-index="1-2" @click="main='add'">用户添加</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="分组2">
              <el-menu-item index="1-3" @click="main=''">站定</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="1-4">
              <template slot="title">选项4</template>
              <el-menu-item index="1-4-1">选项4-1</el-menu-item>
            </el-submenu>
          </el-submenu>
          <el-submenu index="2">
            <template slot="title"><i class="el-icon-menu"></i>导航二</template>
            <el-menu-item-group>
              <template slot="title">分组一</template>
              <el-menu-item index="2-1">选项1</el-menu-item>
              <el-menu-item index="2-2">选项2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="分组2">
              <el-menu-item index="2-3">选项3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="2-4">
              <template slot="title">选项4</template>
              <el-menu-item index="2-4-1">选项4-1</el-menu-item>
            </el-submenu>
          </el-submenu>
          <el-submenu index="3">
            <template slot="title"><i class="el-icon-setting"></i>导航三</template>
            <el-menu-item-group>
              <template slot="title">分组一</template>
              <el-menu-item index="3-1">选项1</el-menu-item>
              <el-menu-item index="3-2">选项2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="分组2">
              <el-menu-item index="3-3">选项3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="3-4">
              <template slot="title">选项4</template>
              <el-menu-item index="3-4-1">选项4-1</el-menu-item>
            </el-submenu>
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-container>
        <el-header style="text-align: right; font-size: 12px">
          <el-dropdown>
            <i class="el-icon-setting" style="margin-right: 15px"></i>
            <el-dropdown-menu slot="dropdown">
              <p  @click="getData">查看/刷新</p>
              <p>新增</p>
              <p>删除</p>
            </el-dropdown-menu>
          </el-dropdown>
        </el-header>
        <!-- 数据显示页面 -->
        <el-main v-if="main === 'admin'">
          <el-table :data="tableData" data-index="1-1">
            <el-table-column prop="name" label="姓名" width="120">
            </el-table-column>
            <el-table-column prop="password" label="密码" width="120">
            </el-table-column>
            <el-table-column prop="radio" label="性别" width="120">
            </el-table-column>
            <el-table-column prop="age" label="年龄" width="120">
            </el-table-column>
            <el-table-column prop="formattedDated" label="日期" width="120">
            </el-table-column>
            <el-table-column prop="className" label="班级名" width="120">
            </el-table-column>
            <el-table-column prop="Iph" label="手机号" width="120">
            </el-table-column>
            <el-table-column prop="Emit" label="电子邮箱" width="120">
            </el-table-column>
          </el-table>
        </el-main>
      </el-container>
    </el-container>
    <!-- 数据库添加用户 -->
     <div class="login-box pos" v-if=" main === 'add'">
      <div class="from admin" v-show="true">
        <el-form ref="form" :model="form" label-width="80px" class="login-box" :rules="rules">
            <el-form-item label="账号" prop="login">
                <el-input v-model="form.login" placeholder="请输入账号"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input type="password" v-model="form.password" placeholder="请输入密码"></el-input>
            </el-form-item>
            <el-form-item label="性别" prop="radio">
                <el-radio v-model="form.radio" label="男">男</el-radio>
                <el-radio v-model="form.radio" label="女">女</el-radio>
            </el-form-item>
            <el-form-item label="年龄" prop="age">
                <el-input v-model="form.age" placeholder="请输入年龄"></el-input>
            </el-form-item>
            <el-form-item label="出生日期" prop="data">
                <el-date-picker v-model="form.data" type="date" placeholder="选择出生日期"> </el-date-picker>
            </el-form-item>
            <el-form-item label="年级" prop="class">
                <el-select v-model="form.class" placeholder="请选择年级">
                    <el-option label="一年级" value="一年级"></el-option>
                    <el-option label="二年级" value="二年级"></el-option>
                    <el-option label="三年级" value="三年级"></el-option>
                    <el-option label="四年级" value="四年级"></el-option>
                    <el-option label="五年级" value="五年级"></el-option>
                    <el-option label="六年级" value="六年级"></el-option>
                    <el-option label="七年级" value="七年级"></el-option>
                    <el-option label="八年级" value="八年级"></el-option>
                    <el-option label="九年级" value="九年级"></el-option>
                    <el-option label="十年级" value="十年级"></el-option>
                </el-select>
            </el-form-item>
            <el-form-item label="电话" prop="Iph">
                <el-input v-model="form.Iph" placeholder="请输入电话"></el-input>
            </el-form-item>
            <el-form-item label="邮箱" prop="Emit">
                <el-input v-model="form.Emit" placeholder="请输入邮箱"></el-input>
            </el-form-item>
            <el-form-item>
                <!-- <el-button type="primary" @click="demo"></el-button> -->
                <!-- <el-button type="primary" @click="onSubmit">立即登录</el-button> -->
                <el-button type="primary" @click="onADmin">立即注册</el-button>
            </el-form-item>
        </el-form>
    </div>
    <!--登陆 -->
     </div>
  </div>
</template>
<script>
import moment from 'moment';
export default {
  name: "SHOE",
  data() {
    return {
      // 获取数据
      form: {
        login: "",
        password: "",
        radio: "",
        age: "",
        data: "",
        class: "",
        Iph: "",
        Emit: "",
      },
      // 标记限制输入内容
      rules: {
        login: [{ required: true, message: "请输入账号", trigger: "blur" }],
        password: [
          { required: true, message: "请输入密码", trigger: "blur", min: 8 },
        ],
        radio: [{ required: true, message: "请输入性别", trigger: "blur" }],
        age: [{ required: true, message: "请输入年龄", trigger: "blur" }],
        data: [{ required: true, message: "请输入出生日期", trigger: "blur" }],
        class: [{ required: true, message: "请输入", trigger: "blur" }],
        Iph: [
          { required: true, message: "请输入手机号", trigger: "blur", max: 11 },
        ],
        Emit: [{ required: true, message: "请输入邮箱", trigger: "blur" }],
      },

      main: "admin",
      tableData: [],
    };
  },
  methods: {
    // 注册
    onADmin() {
      this.$refs.form.validate((value) => {
          if (value && this.form.login.length > 0 && this.form.password.length > 0) {
              const originalDate = this.form.data;
              const formattedDate = moment(originalDate).format('YYYY-MM-DD');
              fetch('http://127.0.0.1:3000/login', {
                  method: 'POST',
                  headers: {
                      'Content-Type': 'application/json'
                  },
                  body: JSON.stringify({
                      login: this.form.login.toString(),
                      password: this.form.password.toString(),
                      radio: this.form.radio.toString(),
                      age: this.form.age.toString(),
                      //出生日期
                      formattedDate: formattedDate,
                      class: this.form.class.toString(),
                      Iph: this.form.Iph.toString(),
                      Emit: this.form.Emit.toString()
                  })
              })
                  .then(response => {
                      if (response) {
                          if (response.status === 200) {
                              alert("注册成功");
                          } else {
                              alert("注册失败");
                          }
                      }
                  })
                  .catch(error => {
                      if (error) {
                          alert("注册失败");
                      }
                  });
          } else {
              alert("请输入您的账号和密码");
          }
      })
  },
    // 获取数据
    getData() {
      const url = "http://127.0.0.1:3000/data";
      console.log("Request URL:", url);
      fetch(url)
        .then((response) => response.json())
        .then((value) => {
          // 处理数据
          const formattedData = value.map((item) => ({
            name: item.NAME,
            password: item.PASSWORD,
            radio: item.RADIO,
            age: item.AGE,
            formattedDated: item.FORMATTEDDATED,
            className: item.CLASSNAME,
            Iph: item.IPH,
            Emit: item.EMIT,
          }));
          this.tableData = formattedData;
        })
        .catch((error) => {
          console.log("Error:", error);
        });
    },
  },
  mounted() {
    this.getData();
  },
};
</script>
<style>
.el-header {
  background-color: #b3c0d1;
  color: #333;
  line-height: 60px;
}

.el-aside {
  color: #333;
}
.login-box {
  width: 350px;
  border: 1px solid #dcdfe6;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 0 30px #dcdfe6;
  background-color: #ffffff;
  margin-left: 150px;
}
.pos {
  position: relative;
  top: -430px;
  left: 90px;
}
</style>

