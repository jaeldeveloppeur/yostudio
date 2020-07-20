<template>
  <div class="container">
      <div class="block">
        <p><span class="text_footer">Currently</span> in Japan_</p>
        <div class="scroll_footer">
            <div class="line_footer"></div>
            <span class="text_footer">Scroll</span>
            <div class="line_footer"></div>
        </div>
        <div class="svg">
            <svg>
                <circle cx="34" cy="34" r="34"></circle>
                <circle id="cercle_percent" cx="34" cy="34" r="34"></circle>
            </svg>
            <div class="plus">
                <div class="plus_horizontal"></div>
                <div class="plus_vertical"></div>
            </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            title: 'test'
        }
    },
    created () {
    window.addEventListener('scroll', this.scrollStyle);
    },
    destroyed () {
    window.removeEventListener('scroll', this.scrollStyle);
    },
    methods: {
        scrollStyle(){
            const cerclePercent = document.getElementById("cercle_percent");
            let scrollTop = window.scrollY;
            let windowHeight = window.innerHeight;
            let scrollHeight = document.body.scrollHeight;
            let scrollPercent = (scrollTop / (scrollHeight - windowHeight)) * 100;
            // console.log(Math.trunc(scrollPercent));
            cerclePercent.style.strokeDashoffset = `calc(220px - (220px * ${Math.trunc(scrollPercent)}) / 100)`;
        }
    }
}
</script>

<style>
.container{
    padding-top: 20px;
    position: fixed;
    bottom: 0;
    background-color: #1c1919;
    width: 100%;
    height: 120px;
}
.block{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-left: 70px;
    margin-right: 70px;
}
circle{
    fill: none;
    stroke-width: 6;
    stroke: #000;
    transform: translate(5px, 5px);
    stroke-dasharray: 220;
    stroke-dashoffset: 220;
}

circle:nth-child(1){
    stroke-dashoffset: 0;
    stroke: #463a3a;
}

circle:nth-child(2){
    stroke-dashoffset: 0;
    stroke: #2863fd;
}

.container p{
    color: #635252;
    font-size: 22px;
}

.svg{
    width: 80px;
    height: 80px;
}

.plus{
    position: absolute;
    top: 57px;
    right: 88px;
}

.plus_horizontal{
    width: 22px;
    border-bottom: 2px solid white ;
}

.plus_vertical{
    width: 22px;
    height: 22px;
    margin-top: -10px;
    margin-left: 10px;
    border-left: 2px solid white;
}

.text_footer{
    font-size: 22px;
    color: white;
}

.scroll_footer{
    display: flex;
    justify-content: center;
    align-items: center;
}
.line_footer{
    width: 140px;
    height: 0px;
    border: 1px solid #463A3A;
}

.line_footer:nth-child(1){
    margin-right: 33px;
}

.line_footer:nth-child(3){
    margin-left: 33px;
}

@media all and (max-width:770px){
    .line_footer{
        width: 50px;
    }
}
</style>
