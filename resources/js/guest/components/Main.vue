<template>
    <main class="main">
        <div class="container">
            <router-view :key="$route.path"></router-view>
        </div>
    </main>
</template>

<script>
export default {
    name: "Main",
};
</script>

<style>
.main {
    background-color: #495057;
    margin-top: 0px;
    padding-bottom: 1px;
}
</style>
