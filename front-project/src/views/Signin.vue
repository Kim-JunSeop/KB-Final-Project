<template>
  <div class="d-lg-flex position-relative h-auto">
    <!-- Home button-->
    <a class="text-nav btn btn-icon bg-light border rounded-circle position-absolute top-0 end-0 p-0 mt-3 me-3 mt-sm-4 me-sm-4" href="/" data-bs-toggle="tooltip" data-bs-placement="left" title="Back to home">
      <i class="ai-home"></i>
    </a>
    <!-- Sign in form-->
    <div class="d-flex flex-column align-items-center w-lg-50 h-auto px-3 px-lg-5 pt-5">
      <div class="w-100 mt-auto" style="max-width: 526px;">
        <h1>로그인</h1>
        <p class="pb-3 mb-3 mb-lg-4">
          아직 계정이 없으신가요? <router-link to="/signup">회원가입</router-link>
        </p>
        <form @submit.prevent="handleSignIn" class="needs-validation" novalidate>
          <div class="pb-3 mb-3">
            <div class="position-relative">
              <i class="ai-mail fs-lg position-absolute top-50 start-0 translate-middle-y ms-3"></i>
              <input v-model="email" class="form-control form-control-lg ps-5" type="email" placeholder="이메일을 입력해주세요" required />
            </div>
          </div>
          <div class="mb-4">
            <div class="position-relative">
              <i class="ai-lock-closed fs-lg position-absolute top-50 start-0 translate-middle-y ms-3"></i>
              <div class="password-toggle">
                <input v-model="password" class="form-control form-control-lg ps-5" type="password" placeholder="비밀번호를 입력해주세요" required />
                <label class="password-toggle-btn" aria-label="Show/hide password">
                  <input type="checkbox" class="password-toggle-check" />
                  <span class="password-toggle-indicator"></span>
                </label>
              </div>
            </div>
          </div>
          <div class="d-flex flex-wrap align-items-center justify-content-between pb-4">
            <div class="form-check my-1">
              <input class="form-check-input" type="checkbox" id="keep-signedin" />
              <label class="form-check-label ms-1" for="keep-signedin">로그인 유지</label>
            </div>
            <router-link class="fs-sm fw-semibold text-decoration-none my-1" to="/forgot-password">비밀번호 찾기</router-link>
          </div>
          <button class="btn btn-lg btn-primary w-100 mb-4" type="submit">로그인</button>
          <h2 class="h6 text-center pt-3 pt-lg-4 mb-4">간편 로그인</h2>
          <div class="row row-cols-1 row-cols-sm-2 gy-3">
            <div class="col">
              <a class="btn btn-icon btn-outline-secondary btn-google btn-lg w-100" href="#"><i class="ai-google fs-xl me-2"></i>Google</a>
            </div>
            <div class="col">
              <a class="btn btn-icon btn-outline-secondary btn-facebook btn-lg w-100" href="#"><i class="ai-facebook fs-xl me-2"></i>Facebook</a>
            </div>
          </div>
        </form>
      </div>
    </div>
    <!-- Cover image-->
    <div class="w-50 bg-size-cover bg-repeat-0 bg-position-center" :style="{ backgroundImage: `url(${coverImage})` }"></div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import coverImage from '@/assets/img/account/cover.jpg';

const email = ref('');
const password = ref('');
const router = useRouter();

const handleSignIn = () => {
  // 여기에 로그인 처리 로직 추가
  console.log('Email:', email.value);
  console.log('Password:', password.value);
  // 로그인 성공 시 원하는 페이지로 이동
  router.push('/dashboard');
};
</script>

<style scoped>
.w-50 {
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
}

</style>