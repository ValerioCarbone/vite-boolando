<script>
import { store } from '../store'
import card from './card.vue'

export default {
    components: {
        card
    },
    data() {
        return {
            store,
            modal: false,
            selectedItem: {}
        }
    },
    methods: {
        showModal(item) {
            this.modal = true
            this.selectedItem = item
        },
        closeModal() {
            this.modal = false
            this.selectedItem = {}
        }
    }
}

</script>

<template>
    <main>
        <div class="shopping">
            <div class="container">
                <div class="row shopping-card">
                    <card v-for="(currentItem, index) in store.products" :key="store.products[index].id" :item="currentItem"
                        @show="showModal" />
                </div>
            </div>
        </div>
    </main>
    <div class="modal" v-if="modal">
        <div class="card">
            <div class="card-header">
                <div class="card-title">{{ selectedItem.name }}</div>
                <span @click="closeModal()" class="closing-icon"> &#10005;</span>
            </div>
            <div class="card-body"></div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.closing-icon:hover {
    cursor: default;
}

.card-header {
    display: flex;
    justify-content: space-between;
}

.shopping-card {
    gap: 0px 15px;
}

.shopping>.container {
    padding: 60px 0;
}

.modal::after {
    content: '';
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 10;
}

.modal .card {
    width: 100%;
    max-width: 600px;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 15;
    border-radius: 15px;
    box-shadow: 0px 0px 30px rgba(0, 0, 0, 0.3);
    padding: 30px;
    background-color: white;
}
</style>