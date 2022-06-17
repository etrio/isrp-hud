<template>
    <div class="stat-wrapper">
        <Icon :shadow="true" class="white--text text--accent-3 mr-1" icon="icon-dollar" :size="13" />
        <span class="cash white--text text--accent-3">{{ value.toLocaleString() }}</span>
    </div>
</template>

<script lang="ts">
import { defineComponent, defineAsyncComponent } from 'vue';
import Icon from '@components/Icon.vue';

const ComponentName = 'Cash';
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
});
</script>

<style scoped>
.stat-wrapper {
    display: flex;
    flex-direction: row;
    justify-content: center;
    justify-items: center;
    align-items: center;
    align-content: center;
    position: relative;
    padding: 3px;
    border-right: solid yellow 4px;
    background-image: linear-gradient(to right, rgba(0,0,0,0), rgba(0,0,0, 0.4));
    width:100%; height: 20px
}

.cash {
    font-family: 'Roboto';
    font-size: 13px;
    font-weight: 600;
    text-shadow: 1px 1px black;
}
</style>
