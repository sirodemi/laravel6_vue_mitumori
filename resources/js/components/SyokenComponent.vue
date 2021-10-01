<template>
    <div class="container">

        <br />
        <div class="alert alert-primary" role="alert">
            Syoken System Mockup
        </div>
        <div class="container">
            <div class="row">
                <div class="col-3">
                    「第一段階」ユーザーレベル
                </div>
                <div class="col">
                    <form>
                        <select id="userLevel" v-model="userLevel" v-on:change="onchange_1stLevel">
                            <option value = "starting">発電機が動かない</option>
                            <option value = "water">水が漏れている</option>
                        </select>
                    </form>
                </div>
            </div>

            <br />
            <div class="row">
                <div class="col-3">
                    「第二段階」推定レベル
                </div>
                <div class="col">
                    <select id="reasonLevel" v-model="reasonLevel" v-on:change="onchange_2ndLevel">
                        <option v-for="(item,key) in reason" :key="key" v-bind:value="item.value">
                            {{ item.text }}
                        </option>
                    </select>
                </div>
            </div>

            <br />
            <div class="row">
                <div class="col-3">
                    「第三段階」作業レベル
                </div>
                <div class="col">
                    <select id="fieldLevel" v-model="fieldLevel" v-on:change="onchange_3rdLevel">
                        <option v-for="(item,key) in field" :key="key" v-bind:value="item.value">
                            {{ item.text }}
                        </option>
                    </select>
                </div>
            </div>

            <br />
            <div class="row">
                <div class="col-3">
                    「第四段階」報告レベル
                </div>
                <div class="col">
                    <form>
                        <label for="recommend">推奨</label>
                        <input type="radio" id="recommend" value="recommend" v-model="report" />
                        <label for="done">　実施済</label>
                        <input type="radio" id="done" value="done" v-model="report" />
                    </form>
                </div>
            </div>

            <br />
            <div class="row">
                <div class="col-3">
                    <button v-on:click="syoken">所見</button>
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
                reasonLevel:'',
                fieldLevel:'',
                reason:'',
                field:'',
                battery:'',
                selected:'',
                options:'',
                measures:'',
                report:'',
            }
        },
        methods:{
            onchange_1stLevel:function(){
                console.log('change93',this.userLevel);
                this.field=[]
                if(this.userLevel == 'starting'){
                    this.reason=[
                        { text: 'バッテリー関係', value: 'starting-1' },
                        { text: '燃料関係', value: 'starting-2' },
                    ]
                }else if(this.userLevel == 'water'){
                    this.reason=[
                        { text: 'ラジエター関係', value: 'water-1' },
                        { text: '冷却水ポンプ関係', value: 'water-2' },
                    ]
                }
            },

            onchange_2ndLevel:function(){
                console.log('change123',this.reasonLevel);
                if(this.reasonLevel == 'starting-1'){
                    this.field=[
                        { text:'バッテリー交換', value: 'batt-1' },
                        { text: 'バッテリー液補充', value: 'batt-2' },
                    ]
                }else if(this.reasonLevel == 'starting-2'){
                    this.field=[
                        { text: '燃料ポンプ修理', value: 'fuel-1' },
                        { text: '燃料ポンプ交換', value: 'fuel-2' },
                    ]
                }else if(this.reasonLevel == 'water-1'){
                    this.field=[
                        { text: 'ラジエター修理', value: 'water-1' },
                        { text: 'ラジエター交換', value: 'water-2' },
                    ]
                }else if(this.reasonLevel == 'water-2'){
                    this.field=[
                        { text: '冷却水ポンプ修理', value: 'pump-1' },
                        { text: '冷却水ポンプ交換', value: 'pump-2' },
                    ]
                }

            },

            onchange_3rdLevel:function(){
                console.log('change140',this.fieldLevel);
            },

            syoken:function(){
                if(this.fieldLevel == 'batt-1' && this.report == 'recommend') this.selected = 'バッテリー交換を推奨します'
                if(this.fieldLevel == 'batt-1' && this.report == 'done') this.selected = 'バッテリー交換を実施しました'
                if(this.fieldLevel == 'batt-2' && this.report == 'recommend') this.selected = 'バッテリー液の補充を推奨します'
                if(this.fieldLevel == 'batt-2' && this.report == 'done') this.selected = 'バッテリー液を入替ました'
                if(this.fieldLevel == 'fuel-1' && this.report == 'recommend') this.selected = '燃料ポンプ修理を推奨します'
                if(this.fieldLevel == 'fuel-1' && this.report == 'done') this.selected = '燃料ポンプ修理を実施しました'
                if(this.fieldLevel == 'fuel-2' && this.report == 'recommend') this.selected = '燃料ポンプの交換を推奨します'
                if(this.fieldLevel == 'fuel-2' && this.report == 'done') this.selected = '燃料ポンプの交換を実施しました'
                if(this.fieldLevel == 'water-1' && this.report == 'recommend') this.selected = 'ラジエターの修理を推奨します'
                if(this.fieldLevel == 'water-1' && this.report == 'done') this.selected = 'ラジエターの修理を実施しました'
                if(this.fieldLevel == 'water-2' && this.report == 'recommend') this.selected = 'ラジエターの交換を推奨します'
                if(this.fieldLevel == 'water-2' && this.report == 'done') this.selected = 'ラジエターを交換しました'
                if(this.fieldLevel == 'pump-1' && this.report == 'recommend') this.selected = '冷却水ポンプの修理を推奨します'
                if(this.fieldLevel == 'pump-1' && this.report == 'done') this.selected = '冷却水ポンプの修理を実施しました'
                if(this.fieldLevel == 'pump-2' && this.report == 'recommend') this.selected = '冷却水ポンプの交換を推奨します'
                if(this.fieldLevel == 'pump-2' && this.report == 'done') this.selected = '冷却水ポンプを交換しました'
            }
        },
        mounted() {
            console.log('Component mounted.')

        }
    }
</script>
