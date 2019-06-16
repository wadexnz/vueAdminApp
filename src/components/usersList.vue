<template>
    <div class='container p-0'>
        <div v-if="isLoading" class="spinner-border" role="status">
            <span class="sr-only">Loading...</span>
        </div>
        <UserItem 
            v-for="user in users"
            v-bind:key="user.id"
            v-bind:info="user"
        ></UserItem>
    </div>
</template>

<script scoped>
    import UserItem from './UserItem.vue'

    export default {
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
        },
        components: {
            UserItem
        },
    }
</script>