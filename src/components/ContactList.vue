<script setup>
import { defineProps, defineEmits } from 'vue';
import EditContact from './EditContact.vue';

const props = defineProps({
    contacts: {
        type: Array,
        Required: true,
    },
    currentContact:{
        type: Object,
        default: null,
    }
})

const emit = defineEmits(['contactDeleted', 'contactEdited'])

const deleteContact = (id) => {
    emit('contactDeleted', id)
}

const Editcontact = (contact) => {
    emit('contactEdited', contact)
}


</Script>
<template>
    <h3>Contact List</h3>
    <ul id="list" class="list">
        <li v-for="contact in contacts" :key="contact.id">
            {{ contact.name }}: {{ contact.phone }}
            <button @click="Editcontact(contact)" class="edit-btn">Edit</button>
            <button @click="deleteContact(contact.id)" class="delete-btn">Delete</button>
            <EditContact v-if="currentContact && contact.id === currentContact.id" :contact ="currentContact" @contactUpdated="emit('contactUpdated', $event)"></EditContact>
        </li>
    </ul>
</template>