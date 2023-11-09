<script>
import { store } from '../store'
import card from './card.vue'

export default {
    components: {
        card
    },
    data() {
        return {
            store
        }
    }
}

</script>

<template>
    <main>
        <div class="shopping">
            <div class="container">
                <div class="row shopping-card">
                    <card v-for="(currentItem, index) in store.products" :key="store.products[index].id"
                        :item="currentItem" />
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped lang="scss">
.shopping-card {
    gap: 0px 15px;
}

.shopping>.container {
    padding: 60px 0;
}
</style>