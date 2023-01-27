<template>
    <div class="backdrop" @click.self="closeModal"> <!-- @click.self -> only register clicks on the element, not its children -->
        <div class="modal" :class="{ sale: theme === 'sale' }">
            <h1>{{ title }}</h1>
            <p><slot>Default Modal Content</slot></p>
            <h2>Links</h2>
            <slot name="links"></slot>
        </div>
    </div>
</template>

<script>
export default {
    props: ["title", "theme"],
    methods : {
        closeModal() {
            this.$emit("close");
        }
    }
}
</script>

<style scoped>
    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: #101a20;
        border-radius: 10px;
        color: white;
    }

    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0.0, 0.0, 0.0, 0.5);
        width: 100%;
        height: 100%;
    }

    h1 {
        color: #00ffc8;
    }

    .modal.sale {
        background: crimson;
        color: white;
    }

    .modal.sale h1 {
        color: white;
    }
</style>
