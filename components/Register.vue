<template>
  <div class="register-container">
    <div class="register-head-group">
      <h1 class="register-header">新規会員登録</h1>
      <h3 class="register-head">初めてご利用の方・会員以外の方</h3>
    </div>
    <div class="register-form">
      <p class="register-content">
        初めてご利用のお客様は、こちらから会員登録を行って下さい。
      </p>
      <validation-observer ref="obs" v-slot="ObserverProps">
        <validation-provider v-slot="{ errors }" rules="required|email">
          <div class="register-email">
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
          <div class="register-password">
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
        <validation-provider v-slot="ProviderProps" rules="required">
          <div class="register-name">
            <label for="name">お名前</label>
            <input v-model="name" id="name" type="text" name="名前" />
          </div>
          <div class="error">{{ ProviderProps.errors[0] }}</div>
        </validation-provider>
        <div class="register-button">
          <button
            type="button"
            :disabled="ObserverProps.invalid || !ObserverProps.validated"
          >
            新規会員登録
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
