<template>
    <div class="col-md-3">
        <div class="card">
            <div class="card-body">
                <h4>{{post.title}}</h4>
                <p>{{post.body}}</p>
            </div>
        </div>
    </div>
</template>

<script> 
export default {
    name: "Card",
    props :{
        post: Object,
    },
}
</script>

<style scoped>
    .card{
        min-height: 200px;
        padding: 10px;
    }
</style>