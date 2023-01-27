<template>
    <h1>{{ title }}</h1>
    <input ref="input"/>
    <h2 ref="inputDisplay"></h2>
    <button @click="updateInput">Update Input Display</button>
    <br/>
    <teleport to="#modals" v-if="showModal">
        <Modal :title="modal_title" theme="sale" @close="toggleModal">
            {{ modal_content }}
            <template v-slot:links>
                <a href="https://github.com">GitHub</a>
                <br/>
                <a href="https://kernel.org">Linux Kernel</a>
            </template>
        </Modal>
    </teleport>
    <button @click.shift="toggleModal">Open Modal (Shift + Click)</button>
</template>

<script>
import Modal from "./components/Modal.vue"

export default {
    name: 'App',
    components: { Modal },
    data() {
        return {
            title: "My First Vue App",
            modal_title: "Modal Title",
            modal_content: "Modal Content",
            showModal: false
        };
    },

    methods: {
        updateInput() {
            this.$refs.inputDisplay.innerText = this.$refs.input.value;
        },

        toggleModal() {
            this.showModal = !this.showModal;
        }
    }
}
</script>

<!-- this style cannot be scoped, because it will be applied on a div outside the component -->
<style>
#app, #modals {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    margin-top: 60px;
}
</style>
