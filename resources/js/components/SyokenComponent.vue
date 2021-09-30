<template>
    <div class="container">

        <br />
        <div class="alert alert-primary" role="alert">
            Syoken System Mockup
        </div>
        <div class="container">
            <div class="row">
                <div class="col-3">
                「バッテリーの症状」を選ぶ
                </div>
                <div class="col">
                    <form>
                        <select id="battery" v-model="battery" v-on:change="onchange">
                            <option>交換</option>
                            <option>バッテリー液補充</option>
                            <option>問題無し</option>
                        </select>
                    </form>
                </div>
            </div>

            <br />
            <div class="row">
                <div class="col-3">
                    <select v-model="selected">
                        <option v-for="(option,key) in options" :key="key" v-bind:value="option.value">
                            {{ option.text }}
                        </option>
                    </select>
                </div>
                <div class="col">
                    <span>Selected: {{ selected }}</span>
                </div>
            </div>
            <br />




        </div>
    </div>
</template>

<script>
    export default {
        data:function(){
            return{
                battery:'',
                selected:'',
                options:''
            }
        },
        methods:{
            onchange:function(){
                console.log('change70',this.battery);
                if(this.battery == '交換'){
                    this.options=[
                        { text: '交換 One', value: '交換A' },
                        { text: '交換 Two', value: '交換B' },
                        { text: '交換 Three', value: '交換C' }
                    ]
                }else{
                    this.options=[
                        { text: '補充 One', value: '液補充A' },
                        { text: '補充 Two', value: '液補充B' },
                        { text: '補充 Three', value: '液補充C' }
                    ]
                }
            }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
