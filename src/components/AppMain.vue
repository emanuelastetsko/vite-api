<script>

export default {
    name: 'AppMain',
}

</script>


<template>

    <main>

        <div class="main-container">
            <select name="type" id="type">
                <option value="alien">Alien</option>
            </select>

            <div class="card-box">
                <div class="card-container">
                    <div class="counter-cards">
                        <span>Found 39 cards</span> 
                    </div>
                    <div class="card">
                        <img src="" alt="">
                        <h5></h5>
                        <span></span>
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
                width: 95%;
                margin: 0 auto;
                padding-top: 30px;
                .counter-cards{
                background-color: #212529;
                color: white;
                padding: 15px 10px;
                }
            }
            

        }
    }
}


</style>