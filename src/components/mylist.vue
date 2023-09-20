<template>
    <div>
            <table class="tab">
                <tr>
                    <th>分类板块</th>
                    <th>直播间名称</th>
                    <th>房间号</th>
                    <th>操作</th>
                </tr>
                <tr v-for="(item,index) in list" :key="index">
                    <td>{{ item.type }}</td>
                    <td>{{ item.name }}</td>
                    <td>{{ item.rooms }}</td>  
                    <td><span class="col" @click="edit(item,index)">编辑</span></td>
                </tr>
            </table>
    </div>
</template>

<script>  
export default {
    props:['list'],
    data() {

        return {};
    },   

    methods: {
        edit(item,index){
            this.$emit('edit',{item,index})
        }
    },
}
</script>

<style lang="scss" scoped>
.tab{
    width: 800px;
    margin: 10px auto;
}
.col{
    color: #4ca5ff;
}
</style>