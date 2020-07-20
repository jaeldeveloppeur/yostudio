<template>
    <div id="welcome">
        <div class="welcome1">
            <h1>Yo > <span id="name_welcome">{{ valeur }}</span></h1>
        </div>
        <div class="welcome2">
            <p>Let's connect, <br> what's your name?</p>
            <input type="text" class="clignoteOff" id="name_user" v-on:click="clignote()">
            <button type="button" v-on:click="test()">test</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            valeur : "Studio",
            count: 0
        }
    },
    methods: {
        test(){
            const studio = document.getElementById('name_welcome').textContent.split('');
            let nameUser = document.getElementById('name_user').value.split('');
            let arrayNameUser = [];
            let j = studio.length;
            let k = 0;
            function letterLogo(){
                studio.pop();
                document.getElementById('name_welcome').textContent = studio.join('');
                j--;
                console.log(j);
                let interval = setTimeout(letterLogo, 50);
                if (j <= 0){
                    clearTimeout(interval);
                    (function addNameUser(){
                        document.getElementById('name_welcome').textContent = arrayNameUser.join('');
                        arrayNameUser.push(nameUser[k]);
                        arrayNameUser[0] = arrayNameUser[0].toUpperCase();
                        k++
                        let interval2 = setTimeout(addNameUser, 135);
                        if(k > nameUser.length){
                            clearTimeout(interval2)
                        }
                    })();
                }
            }
            letterLogo();
        },
        clignote(){
            let i = 0;
            this.count++
            let count = this.count;
            function changeClass(){
                if( i == 0){
                    document.getElementById('name_user').className = "clignote_off"
                    i--
                } else {
                    document.getElementById('name_user').className = "clignote_on"
                    i++
                }
                let clignoteInput = setTimeout (changeClass, 1000)
                if(count > 1){
                    clearTimeout(clignoteInput)
                    console.log('clear')
                }
            }
            changeClass();
        }
    }
}
</script>

<style>
#welcome{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 80vh;
}

.welcome1{
    height: 10rem;
}
.welcome2{
    display: flex;
    flex-direction: column;
    justify-content: center;
    /* align-items: center; */
    height: 200px;
    padding: 2rem;
    background-color: #2863fd;
}
.welcome2 p{
    text-transform: uppercase;
    color: white;
}
.welcome2 button{
    margin-top: 1rem
}
#name_user{
    width: 80%;
    padding-bottom: 0.5rem;
    color: white;
    background-color: #2863FD;
    border-top: 0px solid;
    border-right: 0px solid;
    border-left: 0px solid;
    text-align: left;
    font-size: 1.5rem;
}
.clignote_on{
    border-bottom: 2px solid #93B1FE;
    height: calc(2rem - 2px);
}
.clignote_off{
    border-bottom: 0px solid #93B1FE;
    height: 2rem;
}
</style>