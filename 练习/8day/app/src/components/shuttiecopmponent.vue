<template>
    <div class="warp">
        <!-- 左边内容 -->
        <div class="left" >
            <div class="yes" v-for="(item,index) in arr1">
                <input class="inp" v-model="item.choose"  type="checkbox">{{item.numbe}}</input>
            </div>
        </div>
        <div class="content">
            <button class="top" @click="arr1move" :class="{actives:arr1cal.length ===1}">&gt;&gt;</button>
            <button class="down" @click="arr2move" :class="{active:arr2cal.length === 0}"> &lt;&lt;</button>
        </div>
        <!-- 右边内容 -->
        <div class="right">
            <div class="yes" v-for="(item,index) in arr2">
                <input class="inp" v-model="item.choose" type="checkbox"> {{item.numbe}}</input>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
            data(){
                return{
                    selectindex:0,
                    arr1:[
                    {
                        numbe:"内容1",
                        choose:false
                    },
                    {
                        numbe:"内容2",
                        choose:false
                    },
                    {
                        numbe:"内容3",
                        choose:false
                    },
                    {
                        numbe:"内容4",
                        choose:false
                    },
                    {
                        numbe:"内容5",
                        choose:false
                    },
                    {
                        numbe:"内容6",
                        choose:false
                    },
                    {
                        numbe:"内容7",
                        choose:false
                    }
                    ],      
                    arr2:[
                    {
                        numbe:"内容8",
                        choose:false
                    },
                    {
                        numbe:"内容9",
                        choose:false
                    },
                    {
                        numbe:"内容10",
                        choose:false
                    },
                    {
                        numbe:"内容11",
                        choose:false
                    },
                    {
                        numbe:"内容12",
                        choose:false
                    }
                    ]
                }
            },
            //自动计算器
             computed:{
                    //检测arr1哪一个被选中
                    arr1cal(){
                        return this.arr1.filter(k=>{
                            return k.choose
                        })
                    },
                    //检测arr2哪一个被选中
                    arr2cal(){
                        return this.arr2.filter(k=>{
                            return k.choose
                        })
                    }
                },
                // 方法
                methods:{
                    arr1move(){
                        const save=JSON.parse(JSON.stringify(this.arr1cal))
                        //保留没有没有勾选的选项  
                        this.arr1=this.arr1.filter(k=>{
                            return k.choose===false
                        })
                        save.forEach(k => {
                            k.choose=false
                            this.arr2.push(k)
                        });
                    },
                    arr2move(){
                        const save=JSON.parse(JSON.stringify(this.arr2cal))
                        //保留没有没有勾选的选项  
                        this.arr2=this.arr2.filter(k=>{
                            return k.choose===false
                        })
                        save.forEach(k => {
                            k.choose=false
                            this.arr1.push(k)
                        });
                    }
                }
    }
</script>

<style>
    html,body,div{
            margin: 0px;
            padding: 0px;
        }
        .warp{
            width: 600px;
            height: 400px;
            margin: 80px auto;
            display: flex;
            justify-content: space-between;
        }
        .warp .left{
            border: 1px solid #999;
            width: 250px;
            height: 100%;
            border-radius: 5px;
            display: flex;
            justify-content:space-around;
            flex-direction: column;
            align-items: center;
            overflow: auto;
            background: #eee;
        }
        .warp .content{
            width: 100px;
            height: 80%;
            display: flex;
            justify-content:center;
            flex-direction:column;
            align-items:center;
        }
        .warp .content .top,
        .warp .content .down{
            width: 80px;
            height: 40px;
            text-align: center;
            font-size: 20px;
            border-radius: 10px;
            margin-top: 20px;
        }
        .active{
            color: #fff;
            display: none;
        }
        .actives{
            color: #fff;
        }

        .warp .right{
            border: 1px solid #999;
            width: 250px;
            height: 100%;
            border-radius: 5px;
            display: flex;
            justify-content:space-around;
            flex-direction: column;
            align-items:center;
            overflow: auto;
            background: #eee;
        }
        .warp .yes{
            width: 100%;
            height: 40px;          
        }
        .warp .inp{
            width: 20px;
            height: 20px;
            margin-top: 10px;
            text-align: center;
        }
</style>