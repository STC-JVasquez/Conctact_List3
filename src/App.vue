<script setup>
import Header from './components/Header.vue';
import AddContact from './components/AddContact.vue';
import ContactList from './components/ContactList.vue';
import ContactStats from './components/ContactStats.vue';
import { ref } from 'vue';

const handleAddContact = (contactData) => {
  contacts.value.push({
    id: generateID(),
    name: contactData.name,
    phone: contactData.phone,
  })
}

const handleDeleteContact = (id) => {
  contacts.value = contacts.value.filter((contact) => contact.id !== id)
}

const generateID = () => {
  return Math.floor(Math.random()*10000000)
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