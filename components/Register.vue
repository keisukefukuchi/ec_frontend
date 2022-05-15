<template>
  <div class="register-container">
    <validation-observer ref="obs" v-slot="ObserverProps">
      <validation-provider v-slot="{ errors }" rules="required|min:4|alpha">
        <label for="username">お名前</label>
        <input v-model="username" id="username" type="text" name="名前" />
        <div class="error">{{ errors[0] }}</div>
      </validation-provider>
      <validation-provider v-slot="{ errors }" rules="required|email">
        <label for="email">メールアドレス</label>
        <input v-model="email" id="email" type="email" name="メールアドレス" />
        <div class="error">{{ errors[0] }}</div>
      </validation-provider>
      <validation-provider
        v-slot="{ errors }"
        vid="passwordConfirm"
        rules="required|min:8|alpha_dash"
      >
        <label for="password">パスワード</label>
        <input
          v-model="password"
          id="password"
          type="password"
          name="パスワード"
        />
        <div class="error">{{ errors[0] }}</div>
      </validation-provider>
      <validation-provider
        v-slot="{ errors }"
        rules="confirmed:passwordConfirm"
      >
        <label for="passwordConfirm">パスワード（確認）</label>
        <input
          v-model="passwordConfirm"
          id="passwordConfirm"
          type="password"
          name="確認パスワード"
        />
        <div class="error">{{ errors[0] }}</div>
      </validation-provider>
      <button
        type="button"
        :disabled="ObserverProps.invalid || !ObserverProps.validated"
      >
        送信
      </button>
    </validation-observer>
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
