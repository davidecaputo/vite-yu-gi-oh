<template>
    <div class="d-flex flex-wrap container">
        {{ prova.card_images[0].image_url }}
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: 'HeaderComponent',
        data(){
            return {
                    prova: []
                }
        },
        methods: {
            getElements(){
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=').then((el) => {
                    console.log(el.data.data[0]);
                    this.prova = el.data.data[0];
                });
            }
        },
        mounted(){
            this.getElements();
            console.log(this.prova);
        }
    }
</script>

<style lang="scss" scoped>

</style>