<script setup>
    import{ref, watch, defineProps, defineEmits} from 'vue';

    const props = defineProps({
        contact: {
            type: Object,
            Required: true,
        }
    })
    const emit = defineEmits(['contactUpdated'])

    const name = ref('')
    const phone = ref('')

    watch(() => props.contact, (newContact) => {
        name.value = newContact.name
        phone.value = newContact.phone
    }, {immediate: true})

    const updateContact = () => {
        emit('contactUpdated', {
            id: props.contact.id,
            name: name.value,
            phone: phone.value,
        })
    }
</script>
<template>
    <section>
        <h3>Edit Contact</h3>
        <input type="text" v-model="name" placeholder="Name"/>
        <input type="text" v-model="phone" placeholder="Phone"/>
        <button @click="updateContact">Update</button>
    </section>
</template>