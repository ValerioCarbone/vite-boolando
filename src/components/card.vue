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
            return {}
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
        isSustainable(item) {

            for (let i = 0; i < item.badges.length; i++) {
                if (item.badges[i].type === 'tag') {
                    return item.badges[i].value
                }
            }
        }
    }
}

</script>

<template>
    <div class="col-card ">
        <div class="item-photos">
            <img class="img1" :src="`/img/${item.frontImage}`">
            <img class="img2" :src="`/img/${item.backImage}`">
            <span class="info-card discount" v-show="isDiscounted(item)">{{ isDiscounted(item) }}</span>
            <span class="info-card sosten sosten-pos2" v-show="isSustainable(item)">{{ isSustainable(item) }}</span>
            <span class="heart"> &hearts;</span>
        </div>
        <div class="item-description">
            <p class="marca">{{ item.brand }}</p>
            <p class="item-type">{{ item.name }}</p>
            <p class="price"><span class="discounted-price">14,99 &euro;</span><span class="full-price">{{ item.price }}
                    &euro;</span>
            </p>
        </div>
    </div>
</template>

<style lang="scss" scoped>
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
    text-decoration: line-through;
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
    z-index: 99;
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
</style>