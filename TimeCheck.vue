<template>
    <div>
        <h1>{{result}}</h1>
        <form @submit.prevent="onSubmitForm">
            <input ref="answer" maxlength="4" v-model="inputValue" />
            <button>입력</button>
        </form>
        <div>시도 : {{tries.length}}</div>
        <ul>
            <li v-for="t in tries"><div>{{t.try}}</div><div>{{t.result}}</div></li>
        </ul>
    </div>
</template>

<script>
// 문제를 만든다.
    const getNumbers = () =>{ 
        const nList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];
        const lRtn = [];
        let rNumb = 0;
        for( let i = 0; i < 4; i ++)
        {
            rNumb = Math.floor(Math.random() *(9-i));
            console.log('rNum=', rNumb);
            const cho = nList.splice(rNumb, 1)[0];
            lRtn.push(cho);
        }
        console.log("정답", lRtn);
        return lRtn;
    }
    export default{
        data() {
            return{
                answer: getNumbers(),
                tries: [],
                inputValue: '',
                result: '',
                }
        },
        methods:{
            onSubmitForm(e){
                console.log('입력값:', this.inputValue);
                console.log('정답:', this.answer.join(''));
                if( this.answer.join('') === this.inputValue )
                {
                    console.log('정답입니다.');
                    alert((this.tries.length+1)+'회만에 정답입니다. 초기화 합니다.');
                    this.answer = getNumbers();
                    this.tries = [];
                    this.result = '';
                }
                else
                {
                    console.log('오답입니다.');
                    if( this.tries.length >= 9 )
                    {
                        console.log('game over!!!');
                        alert('게임 기회를 다 사용 했습니다. 초기화 합니다.');
                        this.answer = getNumbers();
                        this.tries = [];
                        this.result = '';
                    }
                    else
                    {

                    }
                }
                this.tries.push({
                    try: this.inputValue,
                    result: 'homerun',
                });
                this.inputValue = '';
                this.$refs.answer.focus();
            }
        }
    }
</script>

<style>

</style>