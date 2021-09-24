<template>
    <div class="container">
        <!-- <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Example Component</div>
                    <div class="card-body">
                        I'm an example component.
                    </div>
                </div>
            </div>
        </div> -->

        <br />
        <div class="alert alert-primary" role="alert">
            Mitumori System Mockup
        </div>
        <div class="container">
            <div class="row">
                <div class="col-3">
                「点検種別」を選ぶ
                </div>
                <div class="col">
                        <form>
                            <select id="tenken" v-model="tenken">
                                <option>C点検</option>
                                <option>F点検</option>
                                <option>負荷試験</option>
                                <option>修理</option>
                            </select>
                        </form>
                </div>
            </div>
            <br />
            <div class="row">
                <div class="col-3">
                「機種」を選ぶ
                </div>
                <div class="col">
                        <form>
                            <select id="os" v-model="type">
                                <option>AP10</option>
                                <option>AP20</option>
                                <option>AY500</option>
                                <option>GT1000</option>
                            </select>
                        </form>
                </div>
            </div>
            <br />
            <div class="row">
                <div class="col-3">
                    「始動方式」を選ぶ
                </div>
                <div class="col">
                    <form>
                        <label for="battery">電気始動</label>
                        <input type="radio" id="battery" value="電気始動" v-model="starting"/>
                        <label for="air">空気始動</label>
                        <input type="radio" id="air" value="空気始動" v-model="starting" />
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data:function(){
            return{
                tenken:'',
                type:'',
                starting:''
            }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
