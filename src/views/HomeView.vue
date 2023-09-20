<template>
  <div>
    <h3>直播间管理</h3>
    <myadd :form="form" @add="add" :flag="flag"></myadd>
    <mylist :list="list" @edit="edit"></mylist>
  </div>
</template>

<script>
import myadd from '../components/myadd.vue'
import mylist from '../components/mylist.vue'
export default {
  data() {
    return {
      active: 0,

      list: JSON.parse(localStorage.getItem('list')) || [
        {
          type: '英雄联盟',
          name: 'lol',
          rooms: '001'
        }
      ],
      form: {
        type: '',
        name: "",
        rooms: '',
      },
      flag: true
    };
  },
  methods: {
    add(val) {
      if (val.type == '' || val.name == '' || val.rooms == '') {
        alert('不能为空')
        return
      } else if (this.flag == true) {//添加
        this.list.push({
          type: val.type,
          name: val.name,
          rooms: val.rooms
        })
      } else {//修改
        this.list.splice(this.active, 1, {
          type: val.type,
          name: val.name,
          rooms: val.rooms
        })
        this.flag=true
      }

      val.type = ''
      val.name = ''
      val.rooms = ''
    },
    edit(val) {
      console.log(val.index);
      this.form.type = val.item.type,
        this.form.name = val.item.name,
        this.form.rooms = val.item.rooms
      this.flag = false
      this.active = val.index
    }
  } ,
  components: {
    myadd,
    mylist
  },
  watch: {
    list: {
      deep: true,
      handler(val) {
        localStorage.setItem('list', JSON.stringify(val))
      }
    },

  },
}
</script>

<style lang="scss" scoped></style>
