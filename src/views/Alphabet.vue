<template>
    <transition name="slide">
        <div
            class="absolute h-screen flex"
            :class="{ '-left-full': showCharacter }"
        >
            <div class="h-full w-screen">
                <div class="w-full grid grid-cols-4 overflow-auto">
                    <router-link
                        v-for="character in alphabet"
                        :key="character.id"
                        :to="{
                            name: 'Alphabet',
                            params: { letterId: character.id },
                        }"
                        class="h-20 w-full inline-flex items-center justify-center text-4xl text-gray-800 bg-white rounded border border-white"
                        :class="{ 'text-red-500': character.vowel }"
                    >
                        {{ character.variants.isolated }}
                    </router-link>
                </div>
            </div>
            <div v-if="showCharacter" class="h-full w-screen">
                <character />
            </div>
        </div>
    </transition>
</template>

<script>
import Vue from 'vue';
import Character from './Character';
import { alphabet } from '~/enums';

export default Vue.extend({
    name: 'Alphabet',
    components: { Character },
    data() {
        return {
            alphabet,
            showCharacter: this.$route.params.letterId,
        };
    },
    watch: {
        $route(to) {
            this.showCharacter = to.params.letterId !== undefined;
        },
    },
    created() {
        console.log('Alphabet created');
    },
});
</script>

<style scoped>
.slide-enter-active,
.slide-leave-active {
    left: 0;
    transition: all 0.5s;
}
.slide-enter, .slide-leave-to /* .fade-leave-active below version 2.1.8 */ {
    left: -100%;
}
</style>
