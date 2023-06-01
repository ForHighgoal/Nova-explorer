<template>
    <span class="novatokenvalue">
        <f-token-value :value="cValue" :decimals="decimals" :number-currency="withPriceCurrency ? 'USD' : undefined"
            :use-placeholder="false" no-currency v-bind="$attrs" />
        <span v-if="!noCurrency"> NOVA</span>
    </span>
</template>

<script>
import FTokenValue from '@/components/core/FTokenValue/FTokenValue.vue';
import { WEIToGLXY } from '@/utils/transactions.js';

export default {
    name: 'nova-token-value',

    components: { FTokenValue },

    props: {
        value: {
            type: [String, Number],
            default: 0,
        },
        decimals: {
            type: Number,
            default: 2,
        },
        /** Convert value to NOVA */
        convert: {
            type: Boolean,
            default: false,
        },
        noCurrency: {
            type: Boolean,
            default: false,
        },
        withPriceCurrency: {
            type: Boolean,
            default: false,
        },
    },

    computed: {
        cValue() {
            return this.convert ? WEIToGLXY(this.value) : this.value;
        },
    },
};
</script>
