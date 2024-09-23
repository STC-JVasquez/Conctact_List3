<script setup>
    import {computed, defineProps} from 'vue';

    const props = defineProps(['contacts'])
    const totalContacts = computed(() => props.contacts.length)
</script>
<template>
    <section class="contact-stats">
        <h3>Number of Contacts</h3>
        <p>Total Contacts: {{ totalContacts}}</p>
    </section>
</template>