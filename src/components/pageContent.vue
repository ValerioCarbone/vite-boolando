<script>
import itemsJson from '../../db.json';
import card from './card.vue';

export default {
    components: {
        card
    },
    data() {
        return {
            itemsDb: itemsJson.products
        }
    },
    created() {
        console.log(this.itemsDb)
    }
}

</script>

<template>
    <main>
        <div class="shopping">
            <div class="container">
                <div class="row shopping-card">
                    <card v-for="currentItem in itemsDb" :key="itemsDb.id" :item="currentItem" />
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