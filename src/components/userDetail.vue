<template>
    <div class="mb-3">
        <div class='row'>
            <span class='col-12 col-md-6'>
                <b>Username: </b> {{detail.username}}
            </span>
            <span class='col-12 col-md-6'>
                <b>Phone: </b> {{detail.phone}}
            </span>
        </div>
        <div class='row'>
            <div class='col-12 col-md-6'>
                <b @click="togAddress = !togAddress" class="detailToggle">Show Address:</b>
                <div v-show="togAddress" class="card mb-0">
                    <div class="card-body">
                        <div 
                            v-for="(value, name) in detail.address"
                            v-bind:key="name"
                        >
                            <b>{{name}}</b>: {{value}}
                        </div>
                    </div>
                </div>
            </div>
            <div class='col-12 col-md-6'>
                <b @click="togCompany = !togCompany" class="detailToggle">Show Company:</b>
                <div v-show="togCompany" class="card mb-0">
                    <div class="card-body">
                        <div 
                            v-for="(value, name) in detail.company"
                            v-bind:key="name"
                        >
                            <b>{{name}}</b>: {{value}}
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['detail'],
        data: function () {
            return {
                togAddress: false,
                togCompany: false
            }
        }
    }
</script>
<style>
    .detailToggle:hover{
        cursor: pointer; 
        text-decoration: underline;
    }
</style>