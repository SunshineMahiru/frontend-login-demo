<template>
  <!-- 外层容器：响应式，PC端居中，移动端带内边距，底色使用 SaaS 经典的 slate-50 -->
  <div class="min-h-screen bg-slate-50 flex items-center justify-center p-4 sm:p-8">
    
    <!-- 登录卡片：最大宽度、圆角、阴影，典型的企业级卡片设计 (UUPM 规范) -->
    <div class="max-w-md w-full bg-white rounded-2xl shadow-xl p-8 space-y-8">
      
      <!-- 头部：Logo占位与欢迎语 -->
      <div class="text-center space-y-2">
        <div class="w-12 h-12 bg-blue-600 rounded-xl flex items-center justify-center mx-auto mb-4 shadow-md shadow-blue-200">
          <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z"></path>
          </svg>
        </div>
        <h2 class="text-2xl font-bold text-gray-900 tracking-tight">欢迎回来</h2>
        <p class="text-sm text-gray-500">请输入您的账号和密码进行登录</p>
      </div>

      <!-- 表单区域 -->
      <form @submit.prevent="handleLogin" class="space-y-5">
        
        <!-- 账号输入框 -->
        <div class="space-y-1">
          <label class="block text-sm font-medium text-gray-700">账号</label>
          <div class="relative">
            <input 
              v-model="formData.account"
              type="text" 
              placeholder="手机号码 / 邮箱"
              class="w-full px-4 py-2.5 border rounded-lg outline-none transition-all duration-200"
              :class="errors.account ? 'border-red-500 focus:ring-2 focus:ring-red-200' : 'border-gray-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-100'"
              @blur="validateAccount"
            />
          </div>
          <!-- 错误提示 -->
          <p v-if="errors.account" class="text-red-500 text-xs mt-1 animate-pulse">{{ errors.account }}</p>
        </div>

        <!-- 密码输入框 -->
        <div class="space-y-1">
          <div class="flex items-center justify-between">
            <label class="block text-sm font-medium text-gray-700">密码</label>
            <a href="#" class="text-xs text-blue-600 hover:text-blue-700 hover:underline transition-colors">忘记密码？</a>
          </div>
          <div class="relative">
            <input 
              v-model="formData.password"
              type="password" 
              placeholder="请输入密码"
              class="w-full px-4 py-2.5 border rounded-lg outline-none transition-all duration-200"
              :class="errors.password ? 'border-red-500 focus:ring-2 focus:ring-red-200' : 'border-gray-300 focus:border-blue-500 focus:ring-2 focus:ring-blue-100'"
              @blur="validatePassword"
            />
          </div>
          <!-- 错误提示 -->
          <p v-if="errors.password" class="text-red-500 text-xs mt-1 animate-pulse">{{ errors.password }}</p>
        </div>

        <!-- 登录按钮 -->
        <button 
          type="submit" 
          class="w-full bg-blue-600 hover:bg-blue-700 text-white font-medium py-2.5 rounded-lg transition-all duration-200 shadow-lg shadow-blue-200 active:scale-[0.98]"
        >
          登 录
        </button>
      </form>

      <!-- 作业要求：个人信息展示区  -->
      <div class="pt-6 border-t border-gray-100 text-center">
        <p class="text-xs text-gray-400 bg-gray-50 py-2 rounded-md">
          <span class="block mb-1 font-medium text-gray-500">🥰欢迎进入登录页面🥰</span>
          姓名：<strong class="text-gray-700">示例</strong> | 学号：<strong class="text-gray-700">示例</strong>
        </p>
      </div>

    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'

// 1. 响应式表单数据
const formData = reactive({
  account: '',
  password: ''
})

// 2. 响应式错误状态
const errors = reactive({
  account: '',
  password: ''
})

// 3. 原生 JS 校验逻辑：账号
const validateAccount = () => {
  const account = formData.account.trim()
  if (!account) {
    errors.account = '账号不能为空'
    return false
  }
  // 简单的长度校验，模拟企业级规则
  if (account.length < 5) {
    errors.account = '账号长度不能少于 5 个字符'
    return false
  }
  errors.account = ''
  return true
}

// 4. 原生 JS 校验逻辑：密码
const validatePassword = () => {
  const pwd = formData.password
  if (!pwd) {
    errors.password = '密码不能为空'
    return false
  }
  if (pwd.length < 6 || pwd.length > 18) {
    errors.password = '密码长度必须在 6-18 位之间'
    return false
  }
  errors.password = ''
  return true
}

// 5. 表单提交处理
const handleLogin = () => {
  // 触发所有校验
  const isAccountValid = validateAccount()
  const isPasswordValid = validatePassword()

  // 只有全部校验通过，才允许"登录"
  if (isAccountValid && isPasswordValid) {
    alert(`登录成功！\n账号：${formData.account}\n（此处在真实开发中将对接 Axios 后端接口）`)
  }
}
</script>