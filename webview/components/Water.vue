<template>
    <div class="stat-wrapper">
        <div class="split space-between">
            <Icon :shadow="true" class="water-icon ml-4" icon="icon-water" :size="18"></Icon>
            <div class="bar">
                <div class="fill" :style="getFill" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, defineAsyncComponent } from 'vue';
import Icon from '@components/Icon.vue';

const ComponentName = 'Water';
export default defineComponent({
    name: ComponentName,
    components: {
        Icon: defineAsyncComponent(() => import('@components/Icon.vue')),
    },
    props: {
        value: {
            type: Number,
            default: 50,
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

.water-icon {
    position: relative;
    z-index: 99;
    opacity: 0.85;

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
    transform: skewX(-10deg);
    margin-top: 2px;
    margin-left: 10px;
    transform: scaleX(-1);
}

.fill {
    position: absolute;
    background: #2196f3;
    z-index: 25;
    height: 100%;
    box-sizing: border-box;
    bottom: 0px;
    border-radius: 5px;
}
</style>
