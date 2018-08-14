<template>
  <div class="layout" style="width: 400px">
    <Layout>
      <Content>
        <Form ref="formInline" :model="formInline" :rules="ruleInline" :label-width="80" >
          <FormItem prop="user" label="用户名">
            <Input type="text" v-model="formInline.user" placeholder="Username" width="100">
            <Icon type="ios-person-outline" slot="prepend"></Icon>
            </Input>
          </FormItem>
          <FormItem prop="password" label="密码">
            <Input type="password" v-model="formInline.password" placeholder="Password">
            <Icon type="ios-lock-outline" slot="prepend"></Icon>
            </Input>
          </FormItem>
          <FormItem>
            <Button type="primary" @click="handleSubmit('formInline')">Signin</Button>
          </FormItem>
        </Form>
      </Content>
    </Layout>
  </div>
</template>

<script>
export default {
  data () {
    return {
      formInline: {
        user: '',
        password: ''
      },
      ruleInline: {
        user: [
          {required: true, message: 'Please fill in the user name', trigger: 'blur'}
        ],
        password: [
          {required: true, message: 'Please fill in the password.', trigger: 'blur'},
          {type: 'string', min: 6, message: 'The password length cannot be less than 6 bits', trigger: 'blur'}
        ]
      }
    }
  },
  methods: {
    handleSubmit (name) {
      this.$refs[name].validate((valid) => {
        if (valid) {
          this.$Message.success('Success!')
        } else {
          this.$Message.error('Fail!')
        }
      })
    }
  }
}
</script>

<style scoped>

</style>
