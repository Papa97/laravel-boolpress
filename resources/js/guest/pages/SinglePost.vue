<template>
    <div>
        <h2>{{ post.title }}</h2>
        <div v-if="post.tags.length > 0">
            <h3>Tag:</h3>
            <ul>
                <li v-for="tag in post.tags" :key="tag.id">
                    {{ tag.name }}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "SinglePost",
    data() {
        return {
            post: {},
        };
    },
    created() {
        axios.get(`/api/posts/${this.$route.params.slug}`).then((response) => {
            this.post = response.data;
        });
    },
};
</script>

<style></style>
