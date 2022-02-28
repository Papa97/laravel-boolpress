<template>
    <header class="header">

        <nav class="navbar navbar-expand-lg">
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarTogglerDemo03" aria-controls="navbarTogglerDemo03" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <a class="navbar-brand" href="/admin/home">Boolpress</a>

            <div class="collapse navbar-collapse">
                <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
                    <li class="nav-item">
                        <router-link :to="{ name: 'home' }" class="nav-link">Home</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link :to="{ name: 'about' }" class="nav-link">Chi siamo</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link :to="{ name: 'categories' }" class="nav-link">Categorie</router-link>
                    </li>
                </ul>
                    <form class="form-inline my-2 my-lg-0">
                    <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
                    <button class="btn btn-outline my-2 my-sm-0" type="submit">Search</button>
                </form>
            </div>
        </nav>
    </header>
</template>

<script>
export default {
    name: "Header",
};
</script>

<style lang='scss' scoped>
.header{
    background-color: #343A40;
}
ul {
    margin-bottom: 0;
    
}
a {
        color:#F8F9FA;
}


button {
    border-color: #ADB5BD;
    color: #ADB5BD; 
}
</style>
