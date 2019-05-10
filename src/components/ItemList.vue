<template>
    <div>
        <div>ItemList</div>
        <div v-for="item in items" :key="item.name">
            <div class="item" :class="{over500: item.price>=500}">
                <div class="name">名前 : {{ item.name }}</div>
                <div class="price">{{ item.price }} 円</div>
                <div v-if="item.price >= 10000">高額商品</div>
            </div>
        </div>
        <div>
            <label for>
                名前
                <input type="text" v-model="NewItemName">
            </label>
            <label for>
                価格
                <input type="number" v-model="NewItemPrice">
            </label>
            <button @click="AddItem">追加</button>
        </div>
    </div>
</template>

<script>
export default {
    name:"ItemList",
    data(){
        return{
            items:[
                {name:"たまご",price:100},
                {name:"りんご",price:160}
            ],
            NewItemName:"",
            NewItemPrice:0
        };
    },
    methods:{
        AddItem(){
            if(this.NewItemName != "" && this.NewItemPrice != 0){
                this.items.push({name : this.NewItemName , price : this.NewItemPrice});
                this.NewItemName="";
                this.NewItemPrice=0;
            }
        }
    }
};
</script>

<style>
.over500{
    color:red;
}
</style>

