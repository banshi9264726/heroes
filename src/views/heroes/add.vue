<template>
  <div>
    <h2 class="sub-header">添加英雄</h2>
    <form>
          <div class="form-group">
            <label for="name">英雄名称</label>
            <input  v-model="formData.name" type="text" class="form-control" id="name" placeholder="请输入英雄姓名">
          </div>
          <div class="form-group">
            <label for="gender">英雄性别</label>
            <input v-model="formData.gender" type="text" class="form-control" id="gender" placeholder="请输入英雄性别">
          </div>
          <button type="submit" class="btn btn-success" @click.prevent="handleAdd">Submit</button>
        </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      formData: {
        name: '',
        gender: ''
      }
    }
  },
  methods: {
    handleAdd () {
      this.$http.post('http://localhost:3000/heroes', this.formData)
        .then((res) => {
          if (res.status === 201) {
            // 添加成功
            // 跳转到列表页
            this.$router.push({
              name: 'heroes'
            })
          }
        })
        .catch((error) => {
          console.log(error)
        })
    }
  }
}
</script>

<style>

</style>
