<script>
export default {}
</script>

<template>
    <footer>
        <div class="container">
            <div class="row justifycon-spacebetween">
                <div class="col-4 footer-info">
                    <h3 class="company-name">Boolando s.r.l.</h3>
                    <a class="links" href="#">Informazioni legali</a>
                    <a class="links" href="#">Informazioni sulla privacy</a>
                    <a class="links" href="#">Diritto di recesso</a>
                </div>
                <div class="col-2 social">
                    Trovaci anche su
                </div>
            </div>
        </div>
    </footer>
</template>

<style scoped lang="scss">
footer {
    background-color: #1A1A1A;
    color: white;

    a {
        display: inline-block;
    }
}

.links {
    font-size: 12px;
    padding-right: 5px;
}

.footer-info {
    padding: 20px 0;
}

.social {
    padding: 20px 0;
}
</style>