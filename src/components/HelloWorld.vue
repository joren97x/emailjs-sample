<script setup>

    import emailjs from '@emailjs/browser'
    import {reactive} from 'vue'

    const form = reactive({
        sendername: '',
        to: '',
        subject: '',
        replyto: '',
        message: ''
    })

    // const sendername = ref('')
    // const to = ref('')
    // const subject = ref('')
    // const replyto = ref('')
    // const message = ref('')

    const send = () => {
        emailjs.send('service_kfsphbh', 'template_xzp03ja', 
        {
            sendername: form.sendername,
            to: form.to,
            subject: form.subject,
            replyto: form.replyto,
            message: form.message
        }
        , 'eEt-YCYeYc0LoTRxJ').then(() => {
            alert('success?')
        })
    }

</script>
<template> 
    <v-container>
        <p class="text-h1 text-center mb-3">Send email</p>
        {{ form }}
        <v-text-field variant="outlined" label="Sender name" v-model="form.sendername"></v-text-field>
        <v-text-field variant="outlined" label="To" v-model="form.to"></v-text-field>
        <v-text-field variant="outlined" label="Subject" v-model="form.subject"></v-text-field>
        <v-text-field variant="outlined" label="Reply to" v-model="form.replyto"></v-text-field>
        <v-textarea variant="outlined" label="Message" v-model="form.message"></v-textarea>
        <v-btn color="blue" @click="send">Send</v-btn>
    </v-container>
</template>