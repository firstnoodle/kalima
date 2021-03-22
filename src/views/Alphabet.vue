<template>
    <transition name="slide">
        <div
            id="cont"
            class="absolute h-screen flex"
            :class="{
                '-left-full': showCharacter,
                'left-0': !showCharacter,
            }"
        >
            <div class="h-full w-screen overflow-auto">
                <router-link
                    v-for="character in alphabet"
                    :key="character.id"
                    :to="{
                        name: 'Alphabet',
                        params: { letterId: character.id },
                    }"
                    class="h-20 w-full grid grid-cols-4 border-b border-gray-100"
                    :class="{
                        'text-indigo-500': character.vowel,
                        'text-gray-600': !character.vowel,
                    }"
                >
                    <div class="flex items-center justify-center text-4xl">
                        {{ character.variants.isolated }}
                    </div>
                    <div class="flex items-center justify-center text-xl">
                        {{ character.name }}
                    </div>
                    <div class="flex items-center justify-center text-xl">
                        {{ character.latinSymbol }}
                    </div>
                    <div class="flex items-center justify-center text-xl">
                        {{ character.ipa }}
                    </div>
                </router-link>
            </div>
            <div class="h-full w-screen">
                <character :id="oldCharacter" />
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
            oldCharacter: 1,
            showCharacter: this.$route.params.letterId,
        };
    },
    watch: {
        $route(to, from) {
            this.showCharacter = to.params.letterId !== undefined;
            this.oldCharacter = to.params.letterId | from.params.letterId;
        },
    },
    created() {
        console.log('Alphabet created');
    },
});
</script>

<style scoped>
#cont {
    transition: all 0.5s;
}
.slide-enter-active,
.slide-leave-active {
    left: 0;
    transition: all 0.5s;
}
.slide-enter, .slide-leave-to /* .fade-leave-active below version 2.1.8 */ {
    left: -100%;
}
</style>
