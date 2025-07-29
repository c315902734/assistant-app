<template>
  <view class="sign-in-page">
    <!-- Status Bar -->
    <view class="status-bar">
      <text class="time">9:41</text>
      <view class="status-icons">
        <view class="network-bars">
          <view class="bar bar-1"></view>
          <view class="bar bar-2"></view>
          <view class="bar bar-3"></view>
          <view class="bar bar-4"></view>
        </view>
        <view class="wifi-icon">
          <text class="icon">📶</text>
        </view>
        <view class="battery-icon">
          <text class="icon">🔋</text>
        </view>
      </view>
    </view>

    <!-- Header -->
    <view class="header">
      <view class="back-button" @tap="goBack">
        <text class="back-arrow">‹</text>
      </view>
      <text class="header-title">Sign in</text>
    </view>

    <!-- Main Content -->
    <view class="main-content">
      <!-- Welcome Section -->
      <view class="welcome-section">
        <text class="welcome-title">Welcome Back Jhon!</text>
        <text class="welcome-subtitle">Sign in to continue</text>
      </view>

      <!-- Form Section -->
      <view class="form-section">
        <!-- Email Input -->
        <view class="input-group">
          <view class="input-container">
            <text class="input-icon">✉</text>
            <input 
              class="input-field" 
              type="text" 
              placeholder="johndoe@mail.com"
              v-model="email"
            />
          </view>
        </view>

        <!-- Password Input -->
        <view class="input-group">
          <view class="input-container">
            <text class="input-icon">🔒</text>
            <input 
              class="input-field" 
              type="password" 
              placeholder="*********************"
              v-model="password"
            />
          </view>
        </view>

        <!-- Remember Me & Forgot Password -->
        <view class="form-options">
          <view class="remember-me" @tap="toggleRemember">
            <view class="checkbox" :class="{ checked: rememberMe }">
              <text v-if="rememberMe" class="checkmark">✓</text>
            </view>
            <text class="remember-text">Remember me</text>
          </view>
          <text class="forgot-password" @tap="forgotPassword">Forget password ?</text>
        </view>

        <!-- Sign In Button -->
        <view class="signin-button" @tap="signIn">
          <text class="signin-text">Sign in</text>
        </view>

        <!-- Sign Up Link -->
        <view class="signup-section">
          <text class="signup-question">Already have not an account? </text>
          <text class="signup-link" @tap="goToSignUp">Sing up !</text>
        </view>
      </view>
    </view>

    <!-- Home Indicator -->
    <view class="home-indicator"></view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      rememberMe: true
    }
  },
  methods: {
    goBack() {
      uni.navigateBack()
    },
    toggleRemember() {
      this.rememberMe = !this.rememberMe
    },
    forgotPassword() {
      uni.showToast({
        title: 'Forgot password clicked',
        icon: 'none'
      })
    },
    signIn() {
      if (!this.email || !this.password) {
        uni.showToast({
          title: 'Please fill in all fields',
          icon: 'none'
        })
        return
      }
      
      uni.showToast({
        title: 'Signing in...',
        icon: 'loading'
      })
      
      // Simulate sign in process
      setTimeout(() => {
        uni.showToast({
          title: 'Sign in successful!',
          icon: 'success'
        })
      }, 1500)
    },
    goToSignUp() {
      uni.showToast({
        title: 'Navigate to Sign Up',
        icon: 'none'
      })
    }
  }
}
</script>

<style>
.sign-in-page {
  min-height: 100vh;
  background: #fff;
  display: flex;
  flex-direction: column;
  font-family: 'Roboto', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}

/* Status Bar */
.status-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 22rpx 30rpx 0;
  height: 60rpx;
}

.time {
  font-weight: 700;
  font-size: 32rpx;
  color: #262b2e;
}

.status-icons {
  display: flex;
  align-items: center;
  gap: 16rpx;
}

.network-bars {
  display: flex;
  align-items: flex-end;
  gap: 6rpx;
  height: 22rpx;
}

.bar {
  width: 6rpx;
  background: #262b2e;
  border-radius: 3rpx;
}

.bar-1 { height: 8rpx; }
.bar-2 { height: 12rpx; }
.bar-3 { height: 18rpx; }
.bar-4 { height: 22rpx; }

.wifi-icon, .battery-icon {
  font-size: 24rpx;
}

/* Header */
.header {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  height: 100rpx;
  background: #fff;
  box-shadow: 0 0 60rpx rgba(50, 214, 216, 0.10);
}

.back-button {
  position: absolute;
  left: 42rpx;
  top: 50%;
  transform: translateY(-50%);
  width: 48rpx;
  height: 48rpx;
  display: flex;
  align-items: center;
  justify-content: center;
}

.back-arrow {
  font-size: 48rpx;
  color: #262b2e;
  font-weight: 300;
}

.header-title {
  font-weight: 700;
  font-size: 44rpx;
  color: #262b2e;
}

/* Main Content */
.main-content {
  flex: 1;
  padding: 0 60rpx;
  display: flex;
  flex-direction: column;
}

/* Welcome Section */
.welcome-section {
  text-align: center;
  margin: 100rpx 0 120rpx;
}

.welcome-title {
  font-weight: 700;
  font-size: 44rpx;
  color: #32d6d8;
  display: block;
  margin-bottom: 24rpx;
}

.welcome-subtitle {
  font-weight: 400;
  font-size: 36rpx;
  color: #262b2e;
  display: block;
}

/* Form Section */
.form-section {
  flex: 1;
}

.input-group {
  margin-bottom: 30rpx;
}

.input-container {
  display: flex;
  align-items: center;
  background: #f4f5f7;
  border-radius: 50rpx;
  height: 100rpx;
  padding: 0 40rpx;
  gap: 24rpx;
}

.input-icon {
  font-size: 32rpx;
  color: #32d6d8;
  width: 36rpx;
  text-align: center;
}

.input-field {
  flex: 1;
  font-size: 32rpx;
  color: #262b2e;
  background: transparent;
  border: none;
  outline: none;
}

.input-field::placeholder {
  color: #999;
}

/* Form Options */
.form-options {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 40rpx 0 60rpx;
}

.remember-me {
  display: flex;
  align-items: center;
  gap: 16rpx;
}

.checkbox {
  width: 32rpx;
  height: 32rpx;
  border-radius: 6rpx;
  background: #32d6d8;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
}

.checkbox.checked {
  background: #32d6d8;
}

.checkmark {
  color: #fff;
  font-size: 20rpx;
  font-weight: bold;
}

.remember-text {
  font-size: 32rpx;
  color: #262b2e;
}

.forgot-password {
  font-size: 32rpx;
  color: #fe724e;
  font-weight: 400;
}

/* Sign In Button */
.signin-button {
  background: #32d6d8;
  border-radius: 50rpx;
  height: 100rpx;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 26rpx 60rpx 0 rgba(50, 214, 216, 0.30);
  margin-bottom: 60rpx;
  transition: all 0.3s ease;
}

.signin-button:active {
  transform: translateY(2rpx);
  box-shadow: 0 20rpx 40rpx 0 rgba(50, 214, 216, 0.20);
}

.signin-text {
  font-weight: 700;
  font-size: 32rpx;
  color: #fffaed;
}

/* Sign Up Section */
.signup-section {
  text-align: center;
  margin-top: auto;
  margin-bottom: 40rpx;
}

.signup-question {
  font-weight: 500;
  font-size: 32rpx;
  color: #262b2e;
}

.signup-link {
  font-weight: 500;
  font-size: 32rpx;
  color: #32d6d8;
}

/* Home Indicator */
.home-indicator {
  width: 268rpx;
  height: 10rpx;
  background: #32d6d8;
  border-radius: 5rpx;
  margin: 0 auto 30rpx;
}

/* Responsive Design */
@media screen and (min-width: 768px) {
  .sign-in-page {
    max-width: 400px;
    margin: 0 auto;
    border: 1px solid #e0e0e0;
    border-radius: 20rpx;
    box-shadow: 0 10rpx 40rpx rgba(0, 0, 0, 0.1);
  }
}

@media screen and (min-width: 1024px) {
  .main-content {
    padding: 0 80rpx;
  }
}
</style>
