<template>
    <div class="card mb-1">
        <div class="card-header row ml-0 mr-0">
            <h3 @click="fetchPosts" class="userToggle mb-0 col-md">
                <i class='cui-user'/>
                {{ " " + info.name }}
            </h3>
            <h3 class="col-md"> 
                <i class='cui-envelope-closed'/>
                {{ " " + info.email }}
            </h3>   
        </div>
        <div v-show="toggleBody" class="card-body">
            <div v-if="isLoading" class="spinner-border" role="status">
                <span class="sr-only">Loading...</span>
            </div>
            <userDetail v-bind:detail="info"/>
            <postView 
                v-for="post in posts"
                v-bind:key="post.id" 
                v-bind:post="post"
            ></postView>
        </div>
    </div>
</template>

<script>
    import postView from "./post"
    import userDetail from "./userDetail"

    export default {
        props: ['info'],
        data: function () {
            return {
                toggleBody: false,
                isLoading: true,
                posts: []
            }
        },
        methods: {
            fetchPosts: function () {
                var vm = this;
                vm.toggleBody = !vm.toggleBody;
                if( vm.posts.length <= 0 ) {
                    fetch('https://jsonplaceholder.typicode.com/posts/?userId=' + vm.info.id)
                        .then(res => res.json())
                        .then(res => {
                            vm.posts = res.splice(0, 10);
                            vm.isLoading = false;
                        });
                }
            }
        },
        components: {
            postView,
            userDetail
        }
    }
</script>
<style>
.userToggle:hover{
    cursor: pointer; 
    text-decoration: underline;
}
i{
    color:darkblue;
}
</style>
