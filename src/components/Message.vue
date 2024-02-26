<template>
    <article class="message" :class="[type !== '' ? 'is-'+type : '']">
        <div v-if="header" class="message-header">
            <p>{{ header }}</p>
            <button class="delete" aria-label="delete" @click="$emit('close')"></button>
        </div>
        <div class="message-body">
            {{ body }}
        </div>
    </article>
</template>

<script>
export default {
    props:
    {
        header: String,
        body: {
            type: String,
            required: true
        },
        type: {
            default: "",
            validator(value, props) {
                // The value must match one of these strings
                return ['', 'dark', 'danger', 'primary', 'link', 'info', 'success', 'warning'].includes(value)
            }
        }
    },
    emits: ["close"]
}
</script>