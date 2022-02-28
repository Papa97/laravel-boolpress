<template>
    <div>
        <h1>{{category.name}}</h1>
    </div>
</template>

<script>
export default {
    name:"SingleCategory",
    data() {
        return {
            category: {},
            posts: []
        }
    },
    created() {
        axios.get(`/api/categories/${this.$route.params.slug}`)
            .then((response) => {
                this.category = response.data;
                
            })
            .catch( (error) => {
                this.$router.push({name: 'page-404'});
            });
            axios.get("/api/posts").then((response) => {
            this.posts = response.data;
        });
    }
}
</script>

<style>

</style>