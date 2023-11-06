<script>
export default {
    data() {
        return {
            logo: '../../public/img/boolean-logo.png',
            iconUser: '../../public/img/user.png',
            iconHeart: '../../public/img/heart.png',
            iconBag: '../../public/img/shopping-bag.png'
        }
    }
}
</script>

<template>
    <header>
        <div class="navbar">
            <div class="container">
                <div class="row justifycon-spacebetween alignitems-center">
                    <div class="col-3">
                        <a class="menu-items" href="#">Donna</a>
                        <a class="menu-items" href="#">Uomo</a>
                        <a class="menu-items" href="#">Bambini</a>
                    </div>

                    <div class="col-3">
                        <div class="logo-container">
                            <figure class="logo">
                                <img :src="logo" alt="logo">
                            </figure>
                        </div>
                    </div>

                    <div class="col-3">
                        <div class="icons-container">
                            <figure class="menu-icons">
                                <img :src="iconUser" alt="">
                            </figure>
                            <figure class="menu-icons">
                                <img :src="iconHeart" alt="">
                            </figure>
                            <figure class="menu-icons">
                                <img :src="iconBag" alt="">
                            </figure>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>

<style scoped lang="scss">
@use '../styles/general.scss';

.navbar {
    background-color: #FF6900;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.42);
    position: fixed;
    top: 0%;
    width: 100%;
    z-index: 1000;
}

.menu-icons {
    display: inline-block;
    max-width: 20px;
    padding-left: 7px;
    margin: 0 5px;
}

.icons-container {
    display: flex;
    justify-content: flex-end;
}

.logo {
    max-width: 140px;
    padding: 18px 0;
}

.menu-items {
    color: white;
    font-weight: 600;
}

.logo-container {
    display: flex;
    justify-content: center;
}
</style>