<template>
    <div class="w-full p-4 font-sans">
        <div class="w-full text-center" style="font-size: 180px">
            {{ character.variants.isolated }}
        </div>
        <div
            class="flex items-center justify-center w-full space-x-4 text-center text-4xl mb-10"
        >
            <div>{{ character.name }}</div>
            <div class="uppercase">{{ character.latinSymbol }}</div>
        </div>

        <div class="grid grid-cols-4 gap-4">
            <div class="text-6xl text-center">
                {{ character.variants.isolated }}
            </div>
            <div class="text-6xl text-center">
                {{ character.variants.final }}
            </div>
            <div class="text-6xl text-center">
                {{ character.variants.medial }}
            </div>
            <div class="text-6xl text-center">
                {{ character.variants.initial }}
            </div>
            <div class="text-center">
                isolated
            </div>
            <div class="text-center">
                final
            </div>
            <div class="text-center">
                medial
            </div>
            <div class="text-center">
                initial
            </div>
        </div>

        <div class="flex items-center space-x-2">
            <!-- <div v-html="character.englishApproximation"></div> -->
        </div>

        <!-- <a :href="character.video" target="_blank" class="block mt-4">
            <svg viewBox="0 0 71.412065 50" width="71.412064" height="50">
                <g id="g5" transform="scale(0.58823529,0.58823529)">
                    <path
                        d="M 118.9,13.3 C 117.5,8.1 113.4,4 108.2,2.6 98.7,0 60.7,0 60.7,0 60.7,0 22.7,0 13.2,2.5 8.1,3.9 3.9,8.1 2.5,13.3 0,22.8 0,42.5 0,42.5 0,42.5 0,62.3 2.5,71.7 3.9,76.9 8,81 13.2,82.4 22.8,85 60.7,85 60.7,85 c 0,0 38,0 47.5,-2.5 5.2,-1.4 9.3,-5.5 10.7,-10.7 2.5,-9.5 2.5,-29.2 2.5,-29.2 0,0 0.1,-19.8 -2.5,-29.3 z"
                        id="path7"
                        style="fill:#282828;fill-opacity:1"
                    />
                    <polygon
                        class="st1"
                        points="80.2,42.5 48.6,24.3 48.6,60.7 "
                        id="polygon9"
                        style="fill:#ffffff"
                    />
                </g>
            </svg>
        </a> -->
    </div>
</template>

<script>
import Vue from 'vue';
import { alphabet } from '~/enums';

export default Vue.extend({
    name: 'Character',
    computed: {
        character() {
            return alphabet.find(letter => {
                return letter.id == this.$route.params.letterId;
            });
        },
    },
});
</script>
