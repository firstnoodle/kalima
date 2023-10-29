<template>
    <div id="app" class="relative w-screen h-screen flex">
        <router-view />
    </div>
</template>

<script>
import Vue from 'vue';
import { alphabet } from '~/enums';

export default Vue.extend({
    name: 'App',
    data() {
        return {
            alphabet,
            showAlphabet: false,
        };
    },
    methods: {
        toggleAlphabetVisibility() {
            this.showAlphabet = !this.showAlphabet;
        },
    },
});
</script>