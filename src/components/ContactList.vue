<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
    contacts: {
        type: Array,
        Required: true,
    }
})

const emit = defineEmits(['contactDeleted'])

const deletContact = (id) => {
    emit('contactDeleted', id)
}


</Script>
<template>
    <h3>Contact List</h3>
    <ul id="list" class="list">
        <li v-for="contact in contacts" :key="contact.id">
            {{ contact.name }}: {{ contact.phone }}
            <button @click="deletContact(contact.id)" class="delete-btn">Delete</button>
        </li>
    </ul>
</template>