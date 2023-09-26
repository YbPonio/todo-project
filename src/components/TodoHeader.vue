<template>
    <header>
        <nav class="container">
            <div class="branding">
                <h1>Vue Todos</h1>
            </div>

            <ul class="nav-routes">
                <RouterLink to="/">Home</RouterLink>
                <RouterLink to="/about">About</RouterLink>
            </ul>
        </nav>
    </header>
</template>

<script setup>
import { RouterLink } from 'vue-router'
</script>

<style lang="scss" scoped>
header {
    background: #355070;

    nav {
    display: flex;
    align-items: center;
    padding: 20px;
    }

    .branding {
        h1 {
            font-size: 3em;
        }
    }

    .nav-routes {
        display: flex;
        flex: 1;
        justify-content: flex-end;
        gap: 3em;
        list-style: none;


        a {
            text-decoration: none;
            color: inherit;
            font-size: 1.5em;
        }
    }
}
</style>