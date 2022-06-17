<template>
    <div class="stat-wrapper">
        <div class="even-split">
        </div>
        <div class="stat-split">
            <div class="speed-wrapper">
                <span class="speed-placeholder">
                    <em>{{ getSpeedPlaceholder }}</em>
                </span>
                <span class="speed">
                    <em>{{ getSpeed }}</em>
                </span>
            </div>
            <div class="stack">
                <div class="split space-between status">
                    <div class="metrics">
                        <em>KMH</em>
                    </div>
                    <div class="seatbelt" :class="getSeatbeltClass">
                        <em><Icon icon="icon-seatbelt-fill" :size="18" id="seatbelt"/></em>
                    </div>
                    <div class="engine" :class="getEngineClass">
                        <em>E</em>
                    </div>
                    <div class="lock" :class="getLockClass">
                        <em>{{ lock ? 'L' : 'U' }}</em>
                    </div>
                    <div class="gear">
                        <em>{{ gear === 0 ? 'R' : gear }}</em>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, defineAsyncComponent } from 'vue';
import Icon from '@components/Icon.vue';

const ComponentName = 'Speedo';
export default defineComponent({
    name: ComponentName,
    components: {
        Icon: defineAsyncComponent(() => import('@components/Icon.vue')),
    },
    props: {
        speed: {
            type: Number,
            required: true,
        },
        isMetric: {
            type: Boolean,
            required: true,
        },
        gear: {
            type: Number,
            required: true,
        },
        engine: {
            type: Boolean,
            required: true,
        },
        seatbelt: {
            type: Boolean,
            required: true,
        },
        fuel: {
            type: Number,
            default: 50,
            required: true,
        },
        lock: {
            type: Boolean,
            required: true,
        },
    },
    computed: {
        getSpeedPlaceholder() {
            if (this.speed.toString().length <= 1) {
                return `00`;
            }

            if (this.speed.toString().length <= 2) {
                return `0`;
            }

            return '';
        },
        getSpeed() {
            return this.speed;
        },
        getEngineClass() {
            if (this.engine) {
                return { 'amber--text': true, 'amber--hover--static': true };
            }

            return { 'grey--text': true };
        },
        getSeatbeltClass() {
            if (this.seatbelt) {
                return { 'amber--text': true, 'amber--hover--static': true };
            }

            return { 'grey--text': true };
        },
        getLockClass() {
            if (this.lock) {
                return { 'orange--text': true, 'orange--hover--static': true };
            }

            return { 'green--text': true, 'green--hover--static': true };
        },
        getFuelStyle() {
            return `width: ${this.fuel}% !important;`;
        },
    },
});
</script>

<style scoped>
.stat-wrapper {
    display: flex;
    flex-direction: column;
    position: relative;
    justify-content: flex-end;
    transform: skewX(10deg);
    min-width: 300px;
    padding-right: 3vw;
    box-sizing: border-box;
}

.stat-split {
    display: flex;
    flex-direction: row;
    position: relative;
    justify-content: flex-start;
}

.even-split {
    display: flex;
    flex-direction: row;
    justify-items: center;
    align-items: center;
}

.speed-wrapper {
    display: flex;
    min-width: 50px;  /* odleglosc predkosci od border*/
    max-width: 100px;
    justify-content: flex-end;
    justify-items: center;
    align-items: center;
    align-content: center;
    padding-right: 5px; /* odleglosc km/h etc od predkosci */
}

.speed,
.speed-placeholder {
    font-family: 'Barlow Semi Condensed', sans-serif;
    font-size: 25px;
    font-weight: 500;
    padding: 0 !important;
    margin: 0 !important;
    line-height: 14px;
    transform: skewX(-5deg);
}

.status {
    min-width: 100px;
}

.speed-placeholder {
    right: 0;
    opacity: 0.5;
    text-shadow: unset !important;
}

.metrics {
    font-family: 'Barlow Semi Condensed', sans-serif;
    font-size: 20px;
    font-weight: 500;
    text-shadow: 1px 1px black;
    transform: skewX(-5deg);
}

.gear,
.seatbelt,
.engine,
.lock {
    font-family: 'Barlow Semi Condensed', sans-serif;
    font-size: 18px;
    font-weight: 500;
    text-shadow: 1px 1px black;
    transform: skewX(-5deg);
}
</style>
