<template>
    <div class='container p-0'>
        <div v-if="isLoading" class="spinner-border" role="status">
            <span class="sr-only">Loading...</span>
        </div>
        <user 
            v-for="user in users"
            v-bind:key="user.id"
            v-bind:info="user"
        ></user>
    </div>
</template>

<script>
    import user from './user.vue'

    export default {
        components: {
            user
        },
        data: function () {
            return {
                users: [],
                isLoading: true
            }
        },
        created: function () {
            var vm = this;
            fetch('https://jsonplaceholder.typicode.com/users')
                .then(res => res.json())
                .then(res => {
                    vm.users = res;
                    vm.isLoading = false;
                });
        }
        
    }
</script>