<template>
    <div>
        <div>To Do List</div>
        <div>
            <table align="center">
                <tr v-for="item in items" :key="item.name" class="item" :class="{uncompleted: item.status==0}">
                    <td class="name">{{ item.name }}</td>
                    <td class="stat">{{ item.status }}</td>
                </tr>
            </table>
        </div>
        <div>
            <label for>
                名前
                <input type="text" v-model="NewTaskName">
            </label>
            <button @click="AddTask">追加</button>
        </div>
    </div>
</template>

<script>
export default {
    name:"to-do-list",
    data(){
        return{
            items:[
                {name:"本を返す",status:0},
                {name:"外に出る",status:1}
            ],
            NewTaskName:"",
            NewTaskStatus:0
        };
    },
    methods:{
        AddTask(){
            if(this.NewTaskName != ""){
                this.items.push({name : this.NewTaskName , status : this.NewTaskStatus});
                this.NewTaskName="";
            }
        }
    }
};
</script>

<style>
.uncompleted{
    color:red;
}
</style>

