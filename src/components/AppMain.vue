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
        },
        selectArchetypeFunction: {
            type: Function,
            default: null
        }
    },
    data(){
        return{
            archetypeFilter: '',
        };
    },
}


</script>


<template>
    <main>

        <div class="main-container">

            <select class="form-select" aria-label="Default select example" @change.native="selectArchetypeFunction">
                <option value="" selected>Select an archetype</option>
                <option :value="archetype" v-for="archetype in cardsArchetypes">{{ archetype }}</option>
            </select>

            <div class="card-box">
                <div class="card-container p-3">
                    <div class="counter-cards">
                        <span>Found {{ cardsCounter }} cards</span> 
                    </div>
                    <div class="row row-cols-5">
                        <div class="col my-card" v-for="card in cardsList">
                            <div class="card-img">
                                <img :src="card.card_images[0].image_url" alt="Card image" class="img-fluid">
                            </div>
                            <div class="card-text text-center">
                                <h3>{{ card.name.toUpperCase() }}</h3>
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
    min-height: calc(100vh - 70px);
    background-color: #d48f38;

    .main-container{
        padding-top: 10px;
        width: 80%;
        margin: 0 auto;
        padding-bottom: 50px;

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
                    min-height: 150px;
                }
            }
        }
    }
}

select{
    width: max-content;
}

h3{
    padding-top: 10px;
    padding-bottom: 15px;
    font-size: 1.5em;
    color: white;
}

</style>