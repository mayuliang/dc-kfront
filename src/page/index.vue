<template>
    <div>
        <el-menu theme="dark" :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
            <el-menu-item index="1" @click=""><router-link to="/">Home</router-link></el-menu-item>
            <el-submenu index="2">
                <template slot="title">我的工作台</template>
                <el-menu-item index="2-1">选项1</el-menu-item>
                <el-menu-item index="2-2">选项2</el-menu-item>
                <el-menu-item index="2-3">选项3</el-menu-item>
            </el-submenu>
            <el-menu-item index="3"><router-link to="/task">Task List</router-link></el-menu-item>
            <el-menu-item index="4">
                <router-link to="/login" v-if="!username">
                    Login
                </router-link>
                <span v-else>
                        用户：{{ username }}
                    </span>
            </el-menu-item>
        </el-menu>
        <router-view></router-view>
    </div>
</template>

<script>
    export default {
        created () {
            this.activeIndex = localStorage.activeIndex
            this.username = document.cookie.substring(9)
        },
        data() {
            return {
                message: "Page App sasdasd",
                activeIndex: '1',
                username: ''
            }
        },
        methods: {
            handleSelect(key, keyPath) {
                console.log(key, keyPath)
                localStorage.activeIndex = key
            }
        }
    }
</script>

<style>

</style>
