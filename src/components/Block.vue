<template>
    <div class="block" v-if="showBlock"  @click="stopTimer">
        click me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return{
            showBlock: false,
            timer: null,
            reaactionTime: 0
        }
    },
    mounted(){
        console.log('mounted run');
        setTimeout(() =>{
            this.startTimer()
            this.showBlock = true
            console.log(this.showBlock);
        }, this.delay)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() =>{
                this.reaactionTime += 10
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            // console.log(this.reaactionTime);
            this.$emit('end', this.reaactionTime)
        }
    },
    updated(){
        console.log("update  run")
    }
}
</script>

<style>
    .block{
        width: 400px;
        background: #0faf87;
        color: white;
        border-radius: 20px;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>