<template>
    <div class="app-container">
        <nav class="navbar">
            <h1 class="logo">🚀 Start Mining & Earn Crypto!</h1>
            <div class="nav-links">
                <router-link to="/" class="nav-link">🏠 Home</router-link>
                <router-link to="/dashboard" class="nav-link">📊 Dashboard</router-link>
                <button v-if="!isLoggedIn" @click="showLoginModal" class="btn">🔑 Login</button>
                <button v-if="isLoggedIn" @click="logout" class="btn btn-logout">🚪 Logout</button>
            </div>
        </nav>

        <div class="main-content">
            <router-view />
        </div>

        <div v-if="isLoginModalVisible" class="modal-overlay">
            <div class="modal-content">
                <h2 class="modal-title">Miner Login</h2>
                <input v-model="username" type="text" placeholder="Username" class="input-box mt-3" />
                <input v-model="password" type="password" placeholder="Password" class="input-box mt-3" />
                <div class="modal-actions">
                    <button @click="login" class="btn w-full">Login</button>
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
                alert("Login Success!");
            } else {
                alert("Please enter username and password!");
            }
        };

        const logout = () => {
            isLoggedIn.value = false;
            alert("Logout Success!");
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
.app-container {
    min-height: 100vh;
    background-color: #1a202c;
    color: #fff;
    display: flex;
    flex-direction: column;
}

.navbar {
    background-color: #2d3748;
    padding: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
        0 2px 4px -1px rgba(0, 0, 0, 0.06);
}

.logo {
    font-size: 1.5rem;
    font-weight: bold;
    color: #63b3ed;
}

.nav-links {
    display: flex;
    gap: 1rem;
}

.nav-link {
    color: #fff;
    padding: 0.5rem 1rem;
    border-radius: 0.25rem;
    text-decoration: none;
    transition: background-color 0.3s;
}

.nav-link:hover {
    background-color: #3182ce;
}

.btn {
    background-color: #4299e1;
    color: #fff;
    padding: 0.5rem 1rem;
    border: none;
    border-radius: 0.25rem;
    cursor: pointer;
    transition: background-color 0.3s;
}

.btn:hover {
    background-color: #3182ce;
}

.btn-logout {
    background-color: #f56565;
}

.main-content {
    flex: 1;
    padding: 1.5rem;
}

.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgba(0, 0, 0, 0.5);
}

.modal-content {
    background-color: #2d3748;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 10px 15px rgba(0, 0, 0, 0.5);
    width: 20rem;
}

.modal-title {
    font-size: 1.25rem;
    font-weight: 600;
    text-align: center;
    color: #fff;
}

.input-box {
    width: 100%;
    padding: 0.5rem 0.75rem;
    margin: 0;
    border: none;
    border-radius: 0.25rem;
    background-color: #4a5568;
    color: #fff;
    outline: none;
}

.input-box:focus {
    box-shadow: 0 0 0 2px #63b3ed;
}

.mt-3 {
    margin-top: 0.75rem;
}

.modal-actions {
    display: flex;
    justify-content: space-between;
    margin-top: 1rem;
}

.w-full {
    width: 100%;
}
</style>