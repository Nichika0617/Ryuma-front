<template>
  <div class="container">
    <p>メールアドレスで登録する．</p>
    <el-steps :active="1">
      <el-step title="Step 1" description="情報入力"></el-step>
      <el-step title="Step 2" description="認証"></el-step>
      <el-step title="Step 3" description="登録完了！"></el-step>
    </el-steps> 
    
    <p>ニックネーム</p>
    
    <el-input placeholder="ユーザー名を入力" v-model="name"></el-input>
    
    <p>パスワード</p>
    <el-input placeholder="パスワードを入力してください" v-model="password" show-password></el-input>
    
    <p>メールアドレス</p>
    <el-input placeholder="メールアドレス" v-model="mail"></el-input>

    <el-button type="primary" style="margin-top: 20px 20px 0 0; ">確認コードを送信</el-button>

      <el-steps :active="2">
        <el-step title="Step 1" description="情報入力"></el-step>
        <el-step title="Step 2" description="認証"></el-step>
        <el-step title="Step 3" description="登録完了！"></el-step>
    </el-steps>
      <p style="margin-top: 40px 40px 0 0;">
        確認コードを入力
      </p>
      <el-input placeholder="確認コードを入力" v-model="code" @input="checkPass"></el-input>

<!--確認コードが一致したら表示する-->
  <transition name="fade">
    <div v-show="show" style="margin-top: 20px 20px 0 0; ">
      <el-steps :active="3">
        <el-step title="Step 1" description="情報入力"></el-step>
        <el-step title="Step 2" description="認証"></el-step>
        <el-step title="Step 3" description="登録完了！"></el-step>
      </el-steps>
      <p style="text-align:center; margin-top: 20px 20px 0 0; ">
        登録完了しました！
      </p>
    </div> 
  </transition>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name:'',
      password:'',
      mail:'',
      code:''
    }
  },
  head(){
    return {
      title: 'メールでサインアップ'
      }
  },
  methods: {
    checkPass: function() {
      this.show = this.code === "1234" /*とりあえず1234てテストしてます，後日正しく改善*/
    }
  },
  created() {
    
  },
}
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
  will-change: opacity;
  transition: opacity 225ms cubic-bezier(0.4, 0, 0.2, 1) 0ms;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>