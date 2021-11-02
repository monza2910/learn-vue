<template>
    <div class="col-md-3">
        <div class="card">
            <div class="card-body">
                <h1>{{post.name}}</h1>
                <h1>{{title}}</h1>
            </div>
        </div>
    </div>
</template>

<script> 
export default {
    name: "Card",
    props :{
        post: Object,
        title: String,
    },
}
</script>

<style>
</style>