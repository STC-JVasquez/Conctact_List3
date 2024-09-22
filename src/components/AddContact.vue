<script setup>
import { ref, defineEmits } from 'vue';

const name = ref('')
const phone = ref('')

const emit = defineEmits(['contactAdded'])

const addContact = () => {
    if(name.value.trim() === '' || phone.value.trim() === ''){
        return
    }
    emit('contactAdded', {
        name: name.value,
        phone: phone.value,
    })

    name.value = ''
    phone.value = ''
}
</script>
<template>
    <section class=" add-contact">
        <h3>Add New Contact</h3>
        <form @submit.prevent="addContact">
            <input type="text" v-model="name" placeholder="Name"/>
            <input type="text" v-model="phone" placeholder="Phone"/>
            <button type="submit">Add Contact</button>
        </form>
    </section>
</template>