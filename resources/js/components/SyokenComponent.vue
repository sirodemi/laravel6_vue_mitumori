<template>
    <div class="container">

        <br />
        <div class="alert alert-primary" role="alert">
            Syoken System Mockup
        </div>
        <div class="container">
            <div class="row">
                <div class="col-3">
                    「症状 1st」ユーザーレベル
                </div>
                <div class="col">
                    <form>
                        <select id="userLevel" v-model="userLevel" v-on:change="onchange_1stLevel">
                            <option value = "1">発電機が動かない</option>
                            <option value = "2">水が漏れている</option>
                        </select>
                    </form>
                </div>
            </div>

            <br />
            <div class="row">
                <div class="col-3">
                    「症状 2nd」推定レベル
                </div>
                <div class="col">
                    <select v-model="selected">
                        <option v-for="(option,key) in options" :key="key" v-bind:value="option.value">
                            {{ option.text }}
                        </option>
                    </select>
                </div>
            </div>



            <div class="row">
                <div class="col-3">
                「症状」
                </div>
                <div class="col">
                    <form>
                        <select id="battery" v-model="battery" v-on:change="onchange">
                            <option>バッテリー経年劣化</option>
                            <option>バッテリー液不足</option>
                        </select>
                    </form>
                </div>
            </div>

            <br />
            <div class="row">
                <div class="col-3">
                    「対策」
                </div>
                <div class="col">
                    <select v-model="selected">
                        <option v-for="(option,key) in options" :key="key" v-bind:value="option.value">
                            {{ option.text }}
                        </option>
                    </select>
                </div>
            </div>

            <br />
            <div class="row">
                <div class="col-3">
                    「所見」
                </div>
                <div class="col">
                    {{ selected }}
                </div>
            </div>

        </div>
    </div>
</template>

<script>
    export default {
        data:function(){
            return{
                userLevel:'',
                battery:'',
                selected:'',
                options:'',
                measures:''
            }
        },
        methods:{
            onchange_1stLevel:function(){
                console.log('change93',this.userLevel);
                if(this.userLevel == '1'){
                    this.options=[
                        { text: 'バッテリー交換　推奨', value: '経年劣化の為、バッテリー交換を推奨します' },
                        { text: 'バッテリー交換　実施', value: '経年劣化の為、バッテリー交換を実施しました' },
                    ]
                }else{
                    this.options=[
                        { text: 'バッテリー液補充　推奨', value: 'バッテリー液の補充を推奨します' },
                        { text: 'バッテリー液補充　実施', value: 'バッテリー液の補充を実施しました' },
                    ]
                }
            },
            onchange:function(){
                console.log('change95',this.battery);
                if(this.battery == 'バッテリー経年劣化'){
                    this.options=[
                        { text: 'バッテリー交換　推奨', value: '経年劣化の為、バッテリー交換を推奨します' },
                        { text: 'バッテリー交換　実施', value: '経年劣化の為、バッテリー交換を実施しました' },
                    ]
                }else{
                    this.options=[
                        { text: 'バッテリー液補充　推奨', value: 'バッテリー液の補充を推奨します' },
                        { text: 'バッテリー液補充　実施', value: 'バッテリー液の補充を実施しました' },
                    ]
                }
            }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
