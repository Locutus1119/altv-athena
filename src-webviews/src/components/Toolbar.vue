<template>
    <div class="toolbar pa-2">
        <div class="split split-full space-between">
            <span class="grey--text overline">
                <slot />
            </span>
            <template v-if="!hideExit">
                <Icon
                    v-if="pageName"
                    class="red--text red--hover hover"
                    @click="closePage"
                    :size="24"
                    icon="icon-times-circle"
                />
                <Icon v-else class="grey--text text--darken-3" :noSelect="true" :size="24" icon="icon-times-circle" />
            </template>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Icon from './Icon.vue';

const ComponentName = 'Toolbar';
export default defineComponent({
    name: ComponentName,
    components: {
        Icon,
    },
    props: {
        pageName: {
            type: String,
            required: false,
        },
        hideExit: {
            type: Boolean,
            default: false,
        },
    },
    methods: {
        closePage() {
            this.$emit('close-page', this.pageName);
        },
    },
});
</script>

<style scoped>
.toolbar {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    justify-items: center;
    align-items: center;
    align-content: center;
    background: rgba(12, 12, 12, 1) !important;
    border-bottom: 2px solid rgba(24, 24, 24, 1);
    width: 100%;
    box-sizing: border-box;
    border-top-left-radius: 6px;
    border-top-right-radius: 6px;
}
</style>
