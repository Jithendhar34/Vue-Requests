<template>
    <h2>Add users</h2>
    <div v-show="loading">
        <app-loader/>
    </div>
    <div v-show="!loading">
        <div class="form-group mb-3">
            <label>Name</label>
            <input class="form-control" type="text" v-model="user.name">
        </div>

        <div class="form-group mb-3">
            <label>Mail</label>
            <input class="form-control" type="email" v-model="user.mail">
        </div>

        <button 
            class="btn btn-primary" 
            @click.prevent="addUser()"
        >Submit</button>
    </div>
</template>

<script setup>
import postUser from '@/composables/postUser';
import { reactive } from 'vue';

const user = reactive({
    name: '',
    mail: '' // Changed from lastname to mail
});

const { loading, addUser } = postUser(user);
</script>
