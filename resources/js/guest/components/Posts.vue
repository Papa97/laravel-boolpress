<template>
    <div>
        <div v-for="post in posts" :key="post.id">
            <h3>{{ post.title }}</h3>
            <p>{{ post.content }}</p>
            
            <div v-if="post.tags.length > 0">
                <ul>
                    <h3>Tag:</h3>
                    <li v-for="tag in post.tags" :key="tag.id">
                        {{tag.name}}
                    </li>
                </ul>
            </div>

            <router-link :to="{ name: 'single-post', params: { slug: post.slug } }">
                Visualizza post
            </router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: "Posts",
    data() {
        return {
            posts: [],
        };
    },

    created() {
        axios.get("/api/posts").then((response) => {
            this.posts = response.data;
        });
    },
};
</script>

<style></style>
