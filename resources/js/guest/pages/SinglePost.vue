<template>
    <div class="single-post">
        <h2>{{ post.title }}</h2>
        <div v-if="post.tags">
            <h3>Tag:</h3>
            <ul>
                <li v-for="tag in post.tags" :key="tag.id">
                    {{ tag.name }}
                </li>
            </ul>
        </div>
        <div>
            <h3>Lascia un commento</h3>
            <form @submit.prevent="addComment()">
                <div class="form-group">
                    <input type="text" id="name" placeholder="Inserisci il nome" v-model="formData.name" class="form-control">
                </div>
                <div class="form-group">
                    <textarea  id="content" cols="80" rows="10" v-model="formData.content" placeholder="Inserisci il commento" class="form-control"></textarea>
                </div>
                <div>
                    <button type="submit" class="btn btn-outline">Aggiungi Commento</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name: "SinglePost",
    data() {
        return {
            post: {},
            formData: {
                name: "",
                content: "",
                post_id: null
            },
            commentSent: false,
            formErrors:{}
        };
    },
    methods: {
        addComment() {


            axios.post(`/api/comments`, this.formData).then((response) => {
                this.formData.name = "";
                this.formData.content = "";
                this.commentSent = true;
            }).catch((error) => {
                this.forErrors = error.response.data.errors;
            })
        }
    },
    created() {
        axios.get(`/api/posts/${this.$route.params.slug}`)
            .then((response) => {
                this.post = response.data;
                this.formData.post_id = this.post.id;
            }).catch((error) => {
                this.$router.push({name: 'page-404'})
            });
    },
};
</script>

<style lang='scss' scoped>
.single-post{
    color: #ADB5BD;
}

button {
    border-color: #ADB5BD;
    color: #ADB5BD; 
}
</style>
