<template>
    <uploader :i18n="i18n"
        v-bind="$attrs"
        v-on="$listeners"
        ref="uploader"/>
</template>

<script>
import Uploader from './Uploader.vue';

export default {
    name: 'EnsoUploader',

    components: { Uploader },

    inject: ['i18n'],

    methods: {
        browseFiles() {
            this.$refs.uploader.browseFiles();
        },
    }
};
</script>
