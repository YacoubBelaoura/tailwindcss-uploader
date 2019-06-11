<template>
    <core-uploader v-bind="$attrs"
        v-on="$listeners"
        ref="uploader">
        <template v-slot:default="{ label, inputBindings, inputEvents, controlEvents }">
            <!-- <form class="is-marginless" -->
            <form class="m-0"
                @submit.prevent>
                <!-- <input class="is-hidden" -->
                <input class=" hidden"
                    v-bind="inputBindings"
                    v-on="inputEvents">
                <slot name="control"
                    :control-events="controlEvents">
                    <!-- <a :class="['file', {'is-small': isSmall}, {'is-large': isLarge}]" -->
                    <a :class="['flex items-stretch justify-start relative', {' text-xs': isSmall}, {'text-2xl': isLarge}]"
                        v-on="controlEvents">
                        <!-- <span :class="['file-cta', {'is-rounded': isRounded}]"> -->
                        <span :class="[' bg-white-smoke text-gray-290', {' rounded-full': isRounded}]">
                            <!-- <span class="file-icon"> -->
                            <span class=" items-center flex h-3 w-3 ltr:mr-1 rtl:ml-1 justify-center">
                                <fa icon="upload"/>
                            </span>
                            <span>
                                {{ label }}…
                            </span>
                        </span>
                    </a>
                </slot>
            </form>
        </template>
    </core-uploader>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core';
import { faUpload } from '@fortawesome/free-solid-svg-icons';
import CoreUploader from '../renderless/Uploader.vue';

library.add(faUpload);

export default {
    name: 'Uploader',

    components: { CoreUploader },

    props: {
        isLarge: {
            type: Boolean,
            default: false,
        },
        isRounded: {
            type: Boolean,
            default: false,
        },
        isSmall: {
            type: Boolean,
            default: false,
        },
    },

    methods: {
        browseFiles() {
            this.$refs.uploader.browseFiles();
        },
    },
};
</script>
// TODO: remove this
// <style lang="scss">
//     .file-cta.is-rounded {
//         border-radius: 290486px;
//     }
// </style>
