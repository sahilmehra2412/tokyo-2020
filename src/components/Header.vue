<template>
    <header>
        <ul>
            <li class="rings">
                <a href="#">
                    <img src="https://olympics.com/images/static/navigation-satellite/navigation-menu-logo.svg"/>
                </a>
            </li>
            <li><a href="#">Home</a></li>
            <li><a href="#">About Us</a></li>
        </ul>
    </header>
</template>

<script>
export default {
    name:'Header'
}
</script>

<style lang="less">
header {
    background: #333;
    ul {
        margin: 0;
        list-style: none;
        display: flex;
        padding: 1em 3em;

        li {
            a{
                text-decoration: none;
                padding: 0 10px;
                color: white;
                font-family: 'Roboto', sans-serif;
            }
            &:nth-child(2){
            margin-left: auto;
        }
        }
    }
    .rings{
        background: white;
        padding: 1em 0.25em;
        position: absolute;
        top: 0;
    }
}
</style>