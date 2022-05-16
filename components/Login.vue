<template>
  <div class="login-container">
    <div class="login-head-group">
      <h1 class="login-header">ログイン</h1>
      <h3 class="login-head">会員のお客様</h3>
    </div>
    <div class="login-form">
      <p class="login-content">
        メールアドレスとパスワードを入力してログインしてください。
      </p>
      <validation-observer ref="obs" v-slot="ObserverProps">
        <validation-provider
          v-slot="{ errors }"
          rules="required|email"
        >
          <div class="login-email">
            <label class="email" for="email">メールアドレス</label>
            <input
              v-model="email"
              id="email"
              type="email"
              name="メールアドレス"
            />
          </div>
          <div class="error">{{ errors[0] }}</div>
        </validation-provider>
        <validation-provider
          v-slot="{ errors }"
          vid="passwordConfirm"
          rules="required|min:8|alpha_dash"
        >
          <div class="login-password">
            <label class="password" for="password">パスワード</label>
            <input
              v-model="password"
              id="password"
              type="password"
              name="パスワード"
            />
          </div>
          <div class="error">{{ errors[0] }}</div>
        </validation-provider>
        <div class="login-button">
          <button
            type="button"
            :disabled="ObserverProps.invalid || !ObserverProps.validated"
          >
            ログイン
          </button>
        </div>
      </validation-observer>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.error {
  color: red;
}
</style>
