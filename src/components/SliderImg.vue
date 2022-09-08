<template>
    <div class="slider">
        <button @click="prev" type="button" class="btn btn-left">
            <img src="../assets/chevron-left.svg" alt="chevron gauche" class="icone">
        </button>
        <div class="container-slides" v-bind:style="{transform : `translateX(${index}px)` , transition : `${transition}` }">
            <img src="../assets/img1.jpeg" class="img-slider">
            <img src="../assets/img2.jpeg" class="img-slider">
            <img src="../assets/img3.jpeg" class="img-slider">
            <img src="../assets/img4.jpeg" class="img-slider">
        </div>
        <button @click="next" type="button" class="btn btn-right">
            <img src="../assets/chevron-right.svg" alt="chevron droite" class="icone">
        </button>
    </div>
</template>

<script>
    export default {
        name : 'SliderImg',
        data : function(){
            return {
                index : 0,
                transition : "transform 0.2s ease"
            }
        },
        methods : {
            next(){
                if(this.index === -1500){
                    this.index = 0
                    this.transition = "none"
                }else {
                    this.transition = "transform 0.2s ease"
                    this.index -= 500
                }
            },
            prev(){
                if(this.index === 0){
                    this.transition = "none"
                    this.index = -1500
                }else {
                    this.transition = "transform 0.2s ease"
                    this.index += 500
                }
            }
        }
    }

</script>


<style scoped>
.slider {
    width: 500px;
    height: 300px;
    margin: 100px auto 0;
    overflow: hidden;
    position: relative;
}
.container-slides {
    display: flex;
}

.img-slider {
    width: 100%;
    height: auto;
}
.btn {
    outline: none;
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    display: block;
    position: absolute;
    z-index: 6000;
    cursor: pointer;
    font-size: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.icone {
    width: 15px;
}
.btn-left {
    top: 50%;
    left: 5px;
    transform: translateY(-50%);
}
.btn-right {
    top: 50%;
    right: 5px;
    transform: translateY(-50%);
}
</style>

