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
                        <select id="battery" v-model="battery">
                            <option>交換</option>
                            <option>バッテリー液補充</option>
                            <option>問題無し</option>
                        </select>
                    </form>
                </div>
            </div>

            <br />
            <!-- <select v-model="selected"> -->
                <!-- <option v-for = "(value, key) in options" v-bind:key="key.val"> -->
                    <!-- <th v-for="(value, key) in columns" :key="key">{{ value }}</th> -->
                        <!-- {{ option.text }} -->
                <!-- </option> -->
            <!-- </select> -->

            <select v-model="selected">
                <option v-for="(option,key) in options" :key="key" v-bind:value="option.value">
                    {{ option.text }}
                </option>
            </select>
            <span>Selected: {{ selected }}</span>


            <br />
            <div class="row">
                <div class="col-3">
                「機種」を選ぶ
                </div>
                <div class="col">
                    <form>
                        <select id="type" v-model="type">
                            <option>AP10</option>
                            <option>AP20</option>
                            <option>AY500</option>
                            <option>GT1000</option>
                        </select>
                    </form>
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
                type:'',
                selected:'',
                options: [
                    { text: 'One', value: 'A' },
                    { text: 'Two', value: 'B' },
                    { text: 'Three', value: 'C' }
                ]
            }
        },

        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
