<template>
    <footer>
        &copy; Olympics {{date}}
    </footer>
</template>

<script>
export default {
    name:'Footer',
    data: function (){
        return {
            date : new Date().getFullYear()
        };
    }
}
</script>

<style>
footer{
    height: 100px;
    line-height: 100px;
    background: #333;
    color: white;
    font-family: 'Roboto';
    text-align: center;
    width: 100%;
}
</style>