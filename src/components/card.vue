<script>
export default {
    props: {
        item: {
            frontImage: {
                type: String,
                required: true
            },
            backImage: {
                type: String,
                required: true
            },
            brand: {
                type: String,
                required: true
            },
            name: {
                type: String,
                required: true
            },
            price: {
                type: Number,
                required: true
            },
            isInFavorites: {
                type: Boolean,
                required: true
            },
            badges: [{
                type: {
                    type: String
                }, value: {
                    type: String
                }
            },
            {
                type: {
                    type: String
                }, value: {
                    type: String
                }
            }]
        },
        data() {
            return {
                store
            }
        }
    },
    methods: {
        isDiscounted(item) {

            for (let i = 0; i < item.badges.length; i++) {
                if (item.badges[i].type === 'discount') {
                    return item.badges[i].value
                }
            }

        },
        getDiscountedPrice() {
            if (this.isDiscounted(this.item)) {
                let a = parseInt(this.isDiscounted(this.item))
                a = Math.abs(a)
                let i = this.item.price - ((this.item.price * a) / 100)
                return i.toFixed(2)
            }
        },
        isSustainable(item) {

            for (let i = 0; i < item.badges.length; i++) {
                if (item.badges[i].type === 'tag') {
                    return item.badges[i].value
                }
            }
        },
        setFavorite() {
            this.item.isInFavorites = !this.item.isInFavorites
        }
    }
}

</script>

<template>
    <div class="col-card ">
        <div class="item-photos">
            <img class="img1" :src="`/img/${item.frontImage}`">
            <img class="img2" :src="`/img/${item.backImage}`">
            <span class="info-card discount" v-if="isDiscounted(item)">{{ isDiscounted(item) }}</span>
            <span class="info-card sosten sosten-pos2" v-show="isSustainable(item)">{{ isSustainable(item) }}</span>
            <span :class="item.isInFavorites === true ? 'favorite' : ''" class="heart" @click="setFavorite()">
                &hearts;</span>
        </div>
        <div class="item-description">
            <p class="marca">{{ item.brand }}</p>
            <p class="item-type" @click=" $emit('show', item)">{{ item.name }}</p>
            <p class="price">
                <span v-if="isDiscounted(item)" class="discounted-price">{{ getDiscountedPrice() }} &euro;</span>
                <span :class="isDiscounted(item) ? 'line-through' : ''" class="full-price">{{ item.price }} &euro;</span>
            </p>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.line-through {
    text-decoration: line-through solid;
}

.item-type:hover,
.heart:hover {
    cursor: default;
}

.item-type:hover {
    text-decoration: underline solid;
}

.heart.favorite:hover {
    color: black;
}

.info-card {
    padding: 4px 8px;
    color: white;
    font-size: 12px;
    font-weight: 600;
}

.discount {
    background-color: red;
    position: absolute;
    left: 0%;
    bottom: 50px;
}


.sosten {
    background-color: green;
}

.sosten-pos2 {
    position: absolute;
    left: 52px;
    bottom: 50px;
}

.item-type {
    font-weight: 500;
    font-size: 18px;
}

.discounted-price {
    color: red;
    font-weight: 600;
    display: inline-block;

}

.full-price {

    display: inline-block;
    padding-left: 3px;
}

.marca {
    font-weight: 300;
}

.price {
    font-size: 14px;

}

.img1 {
    position: relative;
}

.img2 {
    position: absolute;
    z-index: -1;
    top: 0%;
    left: 0%;
}



.heart:hover {
    color: red;
}

.heart {
    background-color: white;
    padding: 0 16px;
    font-size: 34px;
    position: absolute;
    top: 10px;
    right: 0%;
    z-index: 3;
}

.item-photos {
    position: relative;
}

.col-card {
    flex-basis: calc((100% - 30px) / 12 * 4);
    position: relative;
    padding-top: 80px;

    &:hover .img1 {
        z-index: -2
    }
}

.favorite {
    color: red;
}
</style>