<script setup>
import Header from './components/Header.vue';
import AddContact from './components/AddContact.vue';
import ContactList from './components/ContactList.vue';
import { ref } from 'vue';
import ContactStats from './components/ContactStats.vue';

const handleAddContact = (newContact) => {
  contacts.value.push(newContact)
}

const contacts = ref([])
</script>
<template>
  <Header></Header>
  <div>
    <AddContact @contactAdded="handleAddContact"></AddContact>
    <ContactStats :contacts="contacts"></ContactStats>
    <ContactList :contacts="contacts" @contactDeleted="handleDeleteContact"></ContactList>
  </div>
</template>