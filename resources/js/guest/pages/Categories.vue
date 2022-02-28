<template>
    <div class="categories">
        <h1>Categorie</h1>
        <ul>
            <li v-for="category in categories" :key="category.id">
                <router-link :to="{name: 'single-category', params: {slug: category.slug}}">
                    {{category.name}}
                </router-link>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Categories',
    data() {
        return {
            categories: [],
        }
    },
    created() {
        axios.get("/api/categories")
            .then( (response) => {
                this.categories = response.data;
            });
         
    }
}
</script>

<style lang='scss' scoped>
.categories{
    color: #ADB5BD;
    ul {
        padding: 0;
    }
    li {
        list-style: none;
        display: inline-block;
        padding: 0 0 0 10px;
        a {
            color: #ADB5BD;
        }
    }
}
</style>