<template>
    <div class="card mb-1 mt-1">
        <div class="card-header row ml-0 mr-0">
            <h3 @click="fetchPosts" class="userToggle mb-0 col-md">
                <i class='cui-user'/>
                {{ " " + info.name }}
            </h3>
            <h3 class="mb-0 col-md"> 
                <i class='cui-envelope-closed'/>
                {{ " " + info.email }}
            </h3>   
        </div>
        <div v-show="toggleBody" class="card-body">
            <UserDetail v-bind:detail="info"/>
            <div v-if="isLoading" class="spinner-border" role="status">
                <span class="sr-only">Loading...</span>
            </div>
            <PostItem 
                v-for="post in posts"
                v-bind:key="post.id" 
                v-bind:post="post"
            ></PostItem>
        </div>
    </div>
</template>

<script>
    import PostItem from "./PostItem"
    import UserDetail from "./UserDetail"

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
                this.toggleBody = !this.toggleBody;
                if( this.posts.length <= 0 ) {
                    fetch('https://jsonplaceholder.typicode.com/posts/?userId=' + this.info.id)
                        .then(res => res.json())
                        .then(res => {
                            this.posts = res.splice(0, 10);
                            this.isLoading = false;
                        });
                }
            }
        },
        components: {
            PostItem,
            UserDetail
        }
    }
</script>

<style scoped>
    .userToggle:hover{
        cursor: pointer; 
        text-decoration: underline;
    }
    i{
        color:darkblue;
    }
</style>
