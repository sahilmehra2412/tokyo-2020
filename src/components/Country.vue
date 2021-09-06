<template>
    <div class="country" :id="countryData['country_code']">
        <span>{{countryData['rank']}}</span>
        <span class="name" style="flex-grow:1">
            <img :src="flag"/>
            {{countryData['country'] | toUpperCase}}
        </span>
        <span>{{countryData['gold']}}</span>
        <span>{{countryData['silver']}}</span>
        <span>{{countryData['bronze']}}</span>
        <span>{{countryData['total']}}</span>
    </div>
</template>

<script>
export default {
    name:'Country',
    props: ['countryData'],
    data: function(){
        return{
            flag : "https://olympics.com/tokyo-2020/olympic-games/" + this.countryData['flag'],
        }
    },
    filters: {
        toUpperCase: function(text){
            return text.toUpperCase();
        }
    }
}
</script>

<style lang="less">
.country{
    height: 40px;
    display: flex;
    align-items: center;
    font-family: 'Roboto';
    font-size: 1.2em;
    width: 100%;

    span{
        width: 10%;

        &:not(.name){
            text-align: center;
        }
    }

    &:nth-child(2){
        flex-grow: 1;
    }
    &:nth-of-type(2n){
        background: #DAE8E8;
    }
    img{
        height: 18px;
    }
}
#IND{
    bottom: 0;
    position: sticky;
    top: 0;
    height: 50px;
    font-weight: 600;
    font-size: 1.3em;
}

</style>