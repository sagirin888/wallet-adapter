<script lang="ts">
import { Wallet } from "@solana/wallet-adapter-base";
import { defineComponent, PropType } from "vue";
import WalletButton from "./WalletButton.vue";
import WalletIcon from "./WalletIcon.vue";

export default defineComponent({
    name: 'wallet-list-item',
    components: {
        WalletButton,
        WalletIcon,
    },
    props: {
        wallet: Object as PropType<Wallet>,
    },
    setup ({ wallet }) {
        return { wallet };
    },
});
</script>

<template>
    <li>
        <wallet-button @click="$emit('click')">
            <slot>
                {{ wallet.name }}
            </slot>
            <template #end-icon>
                <wallet-icon :wallet="wallet"></wallet-icon>
            </template>
        </wallet-button>
    </li>
</template>
