<template>
    <div>
        <div class="card mb-2 mt-2">
            <h4 @click="toggleBody = !toggleBody" class="card-header postToggle">
                <b>{{post.title}}</b>
            </h4>
            <p v-show="toggleBody" class="card-body">{{post.body}}</p>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['post'],
        data: function () {
            return {
                toggleBody: false
            }
        }
    }
</script>
<style>
.postToggle:hover{
    cursor: pointer; 
    text-decoration: underline;
}
</style>