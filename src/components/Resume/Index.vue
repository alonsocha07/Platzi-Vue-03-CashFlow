<template>
    <main>
        <p>{{ labelVisual }}</p>
        <h1>{{ amountCurrency }}</h1>
        <div class="graphic">
            <slot name="graphic">

            </slot>
        </div>
        <div class="action">
            <slot name="action">

            </slot>
        </div>
    </main>
</template>

<script setup>
import { computed, defineProps } from 'vue';

const currencyFormater = new Intl.NumberFormat("es-CR", {
  style: "currency", currency: "CRC"
})
const props = defineProps({
    totalLabel: {
        type: String,
    }, label: {
        type: String,
    },
    totalAmount: {
        type: Number
    },
    amount: {
        type: Number,
        default: null
    }
});

const amountVisual = computed(() => {
    return props.amount !== null ? props.totalAmount : props.amount
});

const labelVisual = computed(() => {
    return props.label !== null ? props.label : props.totalLabel
});

const amountCurrency = computed(() => {
    return currencyFormater.format(amountVisual.value)
});


</script>

<style scoped>
main {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;
}

h1,
p {
    margin: 0;
    text-align: center;
}

h1 {
    margin-top: 14px;
    color: var(--brand-green);
}

.graphic {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    padding: 48px 24px;
    box-sizing: border-box;
}
</style>