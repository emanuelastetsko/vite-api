<script>

export default {
    name: 'AppMain',
    props: {
        cardsList: {
            type: Array, 
            default: []
        },
        cardsCounter: {
            type: Number,
            default: 0
        },
        cardsArchetypes: {
            type: Array,
            default: []
        }
    }
}

</script>


<template>
    <main>

        <div class="main-container">

            <select class="form-select" aria-label="Default select example">
                <option :value="archetype" v-for="archetype in cardsArchetypes">{{ archetype }}</option>
            </select>

            <div class="card-box">
                <div class="card-container p-3">
                    <div class="counter-cards">
                        <span>Found {{ cardsCounter }} cards</span> 
                    </div>
                    <div class="row row-cols-lg-5">
                        <div class="col my-card" v-for="card in cardsList">
                            <div class="card-img">
                                <img :src="card.card_images[0].image_url" alt="Card image">
                            </div>
                            <div class="card-text">
                                <h3>{{ card.name }}</h3>
                                <h5>{{ card.archetype }}</h5>
                            </div>
                        </div>

                    </div>
                </div>
            </div>

        </div>
    </main>
</template>


<style lang="scss" scoped>

main{
    width: 100%;
    background-color: #d48f38;

    .main-container{
        padding-top: 10px;
        width: 80%;
        margin: 0 auto;

        .card-box{
            background-color: white;
            margin-top: 10px;
            width: 100%;

            .card-container{
                padding-top: 30px;
                overflow: auto;
                .counter-cards{
                background-color: #212529;
                color: white;
                padding: 15px 10px;
                }

                .card-text{
                    background-color: #d48f38;

                }
            }
            

        }
    }
}

select{
    width: max-content;
}



</style>