<template>
    <form @submit.prevent="addfriend">
    <div>
        <label>Name</label>
        <input type="text" v-model="name" />
    </div>
    <div>
        <label>phone</label>
        <input type="text" v-model="phone" />
    </div>
    <div>
        <label>E-mail</label>
        <input type="text" v-model="email" />
    </div>
    <button>Add Friend</button>
</form>
</template>

<script>
export default {
    data(){
        return {
            name:'',
            phone:'',
            email:'',
        }
    },
    methods:{
        addfriend(){
            this.$emit('add-friend',this.name,this.phone,this.email);
        }
    }
}
</script>