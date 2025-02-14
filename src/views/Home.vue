<template>
    <div class="min-h-screen bg-gray-900 text-white flex flex-col">
        <nav class="bg-gray-800 p-4 flex justify-between items-center shadow-md">
            <h1 class="text-2xl font-bold text-blue-400">🚀 Start Mining & Earn Crypto!</h1>
            <div class="space-x-4">
                <router-link to="/" class="nav-link">🏠 首页</router-link>
                <router-link to="/dashboard" class="nav-link">📊 仪表盘</router-link>
                <button v-if="!isLoggedIn" @click="showLoginModal" class="btn">🔑 登录</button>
                <button v-if="isLoggedIn" @click="logout" class="btn bg-red-500">🚪 退出</button>
            </div>
        </nav>

        <!-- 主内容区域 -->
        <div class="flex-grow p-6">
            <router-view />
        </div>

        <!-- 登录弹窗 -->
        <div v-if="isLoginModalVisible" class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50">
            <div class="bg-gray-800 p-6 rounded-lg shadow-lg w-80">
                <h2 class="text-xl font-semibold text-center text-white">用户登录</h2>
                <input v-model="username" type="text" placeholder="用户名" class="input-box mt-3" />
                <input v-model="password" type="password" placeholder="密码" class="input-box mt-3" />
                <div class="flex justify-between mt-4">
                    <button @click="login" class="btn w-full">登录</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { ref } from "vue";

export default {
    setup() {
        const isLoggedIn = ref(false);
        const isLoginModalVisible = ref(false);
        const username = ref("");
        const password = ref("");

        const showLoginModal = () => {
            isLoginModalVisible.value = true;
        };

        const login = () => {
            if (username.value && password.value) {
                isLoggedIn.value = true;
                isLoginModalVisible.value = false;
                alert("登录成功！");
            } else {
                alert("请输入用户名和密码");
            }
        };

        const logout = () => {
            isLoggedIn.value = false;
            alert("已退出登录");
        };

        return {
            isLoggedIn,
            isLoginModalVisible,
            username,
            password,
            showLoginModal,
            login,
            logout,
        };
    },
};
</script>

<style scoped>
.nav-link {
    @apply text-white px-4 py-2 rounded hover:bg-blue-600 transition duration-300;
}

.btn {
    @apply bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition duration-300;
}

.input-box {
    @apply w-full px-3 py-2 rounded bg-gray-700 text-white focus:outline-none focus:ring-2 focus:ring-blue-400;
}
</style>