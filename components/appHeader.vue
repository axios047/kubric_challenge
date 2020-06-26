<template>
    <div class="header-wrap">
        <div class="side-left">
            <div class="branding">
                kubric.
            </div>
            <div class="nav">
                <a href="#">Product</a>
                <a href="#">Pricing</a>
                <a href="#" class="blog">Synapse</a>
                <a href="#">Team</a>
            </div>
        </div>
        <div class="side-right">
            <div class="login-btn">Login</div>
        </div>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
// variables
$base-color: #2E2D2D;
$base-light: #F9F9F9;
$yellow: #FFD341;
$purple: #5C40CF;
$text-color: #1F1F21;
$text-light: #3F3D4C;

.header-wrap{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 3rem;
}
.side-left{
    display: flex;
    align-items: center;
    .branding{
        font-size: 3.052rem;
        font-family: 'Paytone One',sans-serif;
        color: $text-light;
    }
    .nav{
        margin: 0 2rem;
        a{
            font-size: 1.25rem;
            padding: 0 1.5rem;
            text-decoration: none;
            color: $text-color;
        }
        .blog{
            font-family: 'Schoolbell',sans-serif;
        }
    }
}
.login-btn{
    border: 2px solid $purple;
    border-radius: 4px;
    font-size: 1.25em;
    padding: 0.65rem 3rem;
    color: $purple;
    font-weight: bold;
}
@media (max-width: 768px){
    .header-wrap{
        display: none;
    }
}


</style>