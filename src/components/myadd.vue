<template>
    <div>
        <p>分类模块：
            <select name="" id="" class="btn" v-model="form.type">
                <option value="英雄联盟">英雄联盟</option>
                <option value="穿越火线">穿越火线</option>
                <option value="云顶之弈">云顶之弈</option>
            </select>
        </p>
        <p>直播间名称：<input type="text" class="btn" v-model="form.name"></p>
        <p>房间号：<input type="text" class="btn" v-model="form.rooms"></p>
        <button @click="add">{{ flag?'添加':'保存' }}</button>
    </div>
</template>

<script>
export default {
    props:['form','flag'],
data() {
     return {};
},
methods: {
    add(){
        this.$emit('add',this.form)
    }
},
}
</script>

<style lang="scss" scoped>
.btn{
    width: 600px;
    height: 30px;
}
button{
    width: 200px;
    height: 30px;
    background-color: #409eff;
    color: #fff;
    line-height: 30px;
    border: 0;
}

</style>