<template>
    <div>
        <h1>반응속도 체크</h1>
        <div>
            <div>평균시간:{{clickTime}}</div>
            <button @click="timeCheck">클릭</button>
            <div>{{setStartTime}}</div>
        </div>
    
    </div>
</template>

<script>
// 문제를 만든다.

    const getNowTime = () =>{
        return new Date().getTime();
    }
    console.log("time stamp:",getNowTime());
    export default{
        data() {
            return{
                clickTime : 0,
                setStartTime : 0,
                isStart : false,
                }
        },
        methods:{
            timeCheck(e){
                console.log("btn click", this.isStart);
                if(!this.isStart)
                {
                    this.isStart = true;
                    this.setStartTime = getNowTime();
                }
                else
                { 
                    this.isStart = false;

                }
                console.log("start_time:",this.setStartTime);
            }
        }
    }
</script>

<style>
</style>