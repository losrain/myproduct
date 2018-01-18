<template>
<div class="arctice">
  <h1>文章列表<button @click="toAdd">添加文章</button></h1>
  <div>
      <p v-for="(item, key) in arctice" :key = "key">{{item.title}}<span>{{item.createTime}}</span></p>
  </div>
</div>  
</template>


<script>
export default {
  data() {
    return {
      arctice: []
    };
  },
  mounted() {
      this.submitForm();
  },
  methods: {
    toAdd(){
        this.$router.push({name: 'artice'})
    },
    submitForm() {
      var self = this;
      self.$http
        .post("http://localhost:3300/arctice/list")
        .then(function(res) {
          self.arctice = res.data.data;
          console.log(res);
        })
        .catch(function(error) {
          console.log(error);
        });
    }
  }
};
</script>
<style lang="less">
.arctice{
    >div{
        p{
            text-align: left;
            span{
                float: right;
            }
        }
    }
}
</style>