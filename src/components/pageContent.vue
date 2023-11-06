<script>
export default {
    data() {
        return {
            img1: '../../public/img/1.webp',
            img2: '../../public/img/1b.webp'
        }
    }
}



</script>

<template>
    <main>
        <div class="shopping">
            <div class="container">
                <div class="row shopping-card" v-for="n in 6" :key="n">
                    <div class="col-card ">
                        <div class="item-photos">
                            <img class="img1" :src="img1" alt="">
                            <img class="img2" :src="img2" alt="">
                            <span class="info-card discount">-50%</span>
                            <span class="info-card sosten sosten-pos2">Sostenibilità</span>
                            <span class="heart"> &hearts;</span>
                        </div>
                        <div class="item-description">
                            <p class="marca">Levi's</p>
                            <p class="item-type">RELAXED FIT TEE UNISEX</p>
                            <p class="price"><span class="discounted-price">14,99 &euro;</span><span
                                    class="full-price">29,99 &euro;</span></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped lang="scss">
.col-card {
    flex-basis: calc((100% - 30px) / 12 * 4);
    position: relative;
    padding-top: 80px;

}

.shopping-card {
    gap: 0px 15px;
}

.shopping>.container {
    padding: 60px 0;
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

.sosten-pos1 {
    position: absolute;
    left: 0%;
    bottom: 50px;
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

.col-card:hover .img1 {
    z-index: -2
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
</style>