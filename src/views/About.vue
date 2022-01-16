<template>
  <button @click="click">click</button>
  <br />
  <input v-model="this.user.password" />
  <button @click="func">login</button>
</template>
<script>
import axios from "axios";
export default {
  name: "About",
  data() {
    return {
      user: {
        username: "shirj",
        password: "123",
      },
    };
  },
  methods: {
    click() {
      axios.get("http://localhost:8181/user/getById?userId=1").then(
        (response) => {
          console.log(response);
        },
        (error) => {
          console.log(error);
        }
      );
    },
    func() {
      axios.post("http://localhost:8181/user/login", this.user).then(
        () => {
          console.log("登录成功");
        },
        () => {
          console.log("登录失败");
        }
      );
    },
  },
};
</script>
