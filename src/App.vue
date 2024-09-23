<script setup>
import Header from './components/Header.vue';
import AddContact from './components/AddContact.vue';
import ContactList from './components/ContactList.vue';
import ContactStats from './components/ContactStats.vue';
import { ref } from 'vue';

const contacts = ref([])
const currentContact = ref(null)

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

const handleEditContact = (contact) => {
  currentContact.value = contact
}

const handleUpdateContact = (updatedContact) =>{
  const index = contacts.value.findIndex((c) => c.id === updatedContact.id)
  if (index !== -1){
    contacts.value[index] = updatedContact
    currentContact.value = null
  }
}

const generateID = () => {
  return Math.floor(Math.random()*10000000)
}



</script>
<template>
  <Header></Header>
  <div>
    <AddContact @contactAdded="handleAddContact"></AddContact>
    <ContactStats :contacts="contacts"></ContactStats>
    <ContactList :contacts="contacts" :currentContact="currentContact" @contactDeleted="handleDeleteContact" @contactEdited="handleEditContact" @contactUpdated="handleUpdateContact"></ContactList>
  </div>
</template>