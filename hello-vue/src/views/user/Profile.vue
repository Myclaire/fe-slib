<template>
  <!-- 所有的页面内容必须在标签下，不能直接在根节点下 -->
  <div>
    <h1>个人信息</h1>
    <h1>{{ $route.params.id }}</h1>
    <h1>{{id}}</h1>
  </div>
</template>

<script>
  export default {
    props: ['id'],
    name: "UserProfile",
    //相当于拦截器
    beforeRouteEnter:(to,from,next)=>{
      console.log("进入路由之前");//加载数据
      next(vm => {
        vm.getData();//进入路由之前执行方法
      });
    },
    beforeRouteLeave:(to,from,next)=>{
      console.log("进入路由之后");
      next();
    },
    methods: {
      getData: function () {
        this.axios({
          method: 'get',
          url: 'http://localhost:8080/static/mock/data.json'
        }).then(function (response) {
          console.log(response)
        })
      }
    }
  }
</script>

<style scoped>

</style>
