<template>
    <div class="stat-wrapper">
        <div class="split space-between">
            <Icon :shadow="true" class="armour-icon ml-4" icon="icon-shield2" :size="18"></Icon>
            <div class="bar">
                <div class="fill" :style="getFill" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, defineAsyncComponent } from 'vue';
import Icon from '@components/Icon.vue';

const ComponentName = 'Armour';
export default defineComponent({
    name: ComponentName,
    components: {
        Icon: defineAsyncComponent(() => import('@components/Icon.vue')),
    },
    props: {
        value: {
            type: Number,
            default: 199,
        },
    },
    computed: {
        getFill() {
            return `width: ${this.value}% !important`;
        },
    },
});
</script>

<style scoped>
.stat-wrapper {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    position: relative;
    right: -50px;
}

.armour-icon {
    position: relative;
    z-index: 99;
    opacity: 0.85;
    margin-right: 3px;
}

.bar {
    display: block;
    position: relative;
    background: rgba(136, 136, 136, 0.5);
    box-sizing: border-box;
    min-width: 75px;
    max-width: 75px;
    min-height: 10px;
    max-height: 10px;
    border-radius: 5px;
    margin-top: 2px;
    margin-left: 10px;
    transform: scaleX(-1);
}

.fill {
    position: absolute;
    background: #eeeeee;
    z-index: 25;
    height: 100%;
    box-sizing: border-box;
    bottom: 0px;
    border-radius: 5px;
}
</style>
