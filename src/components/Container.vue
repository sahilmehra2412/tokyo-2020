<template>
    <div class="cont">
        <div class="nav">
            Tokyo 2020
        </div>
        <div id="head">
            <span>S.no.</span>
            <span class="name" style="flex-grow:1">Country</span>
            <span>Gold</span>
            <span>Silver</span>
            <span>Bronze</span>
            <span>Total</span>
        </div>
        <template v-for="country of countries">
            <Country v-bind:key="country['rank']" :country-data="country"/>
        </template>
    </div>
</template>

<script>
import Country from './Country.vue';

export default {
    name:'Container',
    components: {
        Country
    },
    data: function(){
        return{
            countries : [],
        }
    },
    created: function(){
        const url = "https://olympics.com/tokyo-2020/olympic-games/en/results/all-sports/medal-standings.htm";
        fetch(url).then(res=>{
            return res.text()
        }).then(result=>{
            const dom = new DOMParser();
            const html = dom.parseFromString(result,'text/html');
            const tbody = html.getElementsByTagName('tbody');
            const elements = tbody[0].children;
            elements.forEach((element, index) => {
                let obj = {};
                let gold = 0;
                let silver = 0;
                let bronze = 0;
                element.children.forEach(elem=>{
                    const name = elem.getAttribute('data-text');
                    if (elem?.children[0]?.getAttribute('title')?.includes('Gold')){
                        gold = parseInt(elem?.children[0].text);
                    }
                    if (elem?.children[0]?.getAttribute('title')?.includes('Silver')){
                        silver = parseInt(elem?.children[0].text);
                    }
                    if (elem?.children[0]?.getAttribute('title')?.includes('Bronze')){
                        bronze = parseInt(elem?.children[0].text);
                    }
                    obj['rank'] = index+1;
                    if (name){
                        obj['country'] = name
                        obj['country_code'] = elem.children[0].getAttribute('country');
                        const img = elem.children[0].children[0].children[0].getAttribute('src').substring(8);
                        obj['flag'] = img;
                    }
                    obj['gold'] = gold;
                    obj['silver'] = silver;
                    obj['bronze'] = bronze;
                    obj['total'] = gold + silver + bronze;
                })
                this.countries.push(obj);
            });
        })
    }
}
</script>

<style lang="less">
#head{
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
    &>span{
        font-weight: 700;
    }
}
.nav{
    height: 40px;
    width: 100%;
    text-align: center;
    background: rgba(0, 0, 0, 0.1);
    line-height: 40px;
    font-size: 24px;
    font-weight: 600;
    font-family: 'Roboto';
    color: #383645;
}
</style>