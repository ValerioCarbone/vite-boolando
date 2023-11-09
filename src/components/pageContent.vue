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
        },
        isDiscounted(item) {

            for (let i = 0; i < item.badges.length; i++) {
                if (item.badges[i].type === 'discount') {
                    return item.badges[i].value
                }
            }

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
                <div class="card-title">
                    <h3>{{ selectedItem.name }}</h3>
                </div>
                <span @click="closeModal()" class="closing-icon"> &#10005;</span>
            </div>
            <div class="card-body">
                <div class="col-6">
                    <img :src="`./img/${selectedItem.frontImage}`" alt="">
                </div>
                <div class="col-6 card-text">
                    <p>
                        Brand :
                    <h4>{{ selectedItem.brand }}</h4>
                    </p>
                    <p>
                        Price :
                    <h4>{{ selectedItem.price }} &euro;</h4>
                    </p>
                    <p v-if="isDiscounted(selectedItem)">Discount :
                    <h4>{{ isDiscounted(selectedItem) }}</h4>
                    </p>
                    <p v-if="isDiscounted(selectedItem)">
                        Discounted price :
                    <h4>14,99 &euro;</h4>
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.col-6 {
    flex-basis: calc(100% / 2);
}

.card-body {
    display: flex;
    flex-wrap: nowrap;

    .col-6 {
        padding-top: 16px;

        img {
            border: 1px solid rgba(0, 0, 0, 0.3);
        }
    }


    .col-6.card-text {
        text-align: center;
        line-height: 24px;
        display: flex;
        flex-direction: column;
        justify-content: space-around;

        h4 {
            font-size: 26px;
        }


    }


}

.card-title {
    flex-grow: 1;
    text-align: center;
    font-weight: 500;
    font-size: 28px;
}

.closing-icon:hover {
    cursor: default;
}

.card-header {
    display: flex;
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
    padding: 20px;
    background-color: white;
}
</style>