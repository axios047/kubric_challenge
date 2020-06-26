<template>
    <div class="footer-wrap">
        <div class="top-content">
            <div class="col links">
                <div class="title">CONTACT</div>
                <a href=""><p>Contact Us</p></a>
            </div>
            <div class="col links">
                <div class="title">PRODUCT</div>
                <a href=""><p>Features</p></a>
                <a href=""><p>Pricing</p></a>
                <a href=""><p>FAQ</p></a>
            </div>
            <div class="col links">
                <div class="title">PEOPLE</div>
                <a href="" class="hand"><p>Ramblings</p></a>
                <a href=""><p>Teams</p></a>
                <a href=""><p>Jobs</p></a>
            </div>
            <div class="col news">
                <h3 class="title">Subscribe to <strike>our blog</strike></h3>
                <p>The latest updates, news, resources sent straight to your inbox</p>
                <div class="inputs">
                    <input type="text" placeholder="Enter your e-mail">
                    <div class="next">-></div>
                </div>
            </div>
        </div>
        <div class="botton-content"></div>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
// variables
$base-color: #2E2D2D;
$yellow: #FFD341;
$purple: #5C40CF;
$text-color: #1F1F21;
$text-light: #3F3D4C;

.footer-wrap{
    width: 100%;
}

.top-content{
    display: flex;
    margin: 0 auto;
    justify-content: space-between;
    max-width: 90rem;
    padding: 3rem 0;
    .col{
        padding: 1rem;
        border-left: 2px solid $yellow;
    }
    .links{
        .title{
            font-family: 'Schoolbell',sans-serif;
            font-size: 1.563rem;
            padding: 0.25rem 0.5rem;
            background: $yellow;
            text-align: center;
        }
        a{
            font-size: 1.25rem;
            text-decoration: none;
            color: inherit;
            padding: 1rem;
        }
        .hand{
            font-family: 'Schoolbell',sans-serif;
        }
    }
    .news{
        .title strike{
            text-decoration-color: $yellow;
            position: relative;
        }
        .title strike::before{
            content: 'Synapse';
            position: absolute;
            font-family: 'Schoolbell',sans-serif;
            top: 0;
            left: 0;
            transform: translateY(-80%);
        }
    }
}
@media (max-width: 768px){
    .footer-wrap{
        display: none;
    }
}

</style>