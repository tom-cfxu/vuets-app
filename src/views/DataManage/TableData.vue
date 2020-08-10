<template>
  <div class="TableData">
      你好
  </div>
</template>

<script lang="ts">
import {Component,Vue, Provide} from 'vue-property-decorator'
@Component({
    components:{} 
})
export default class TableData extends Vue {
  @Provide() searchVal:string=''; //搜索框
  @Provide() tHeight:number= document.body.offsetHeight-270;
  @Provide() tableData:any = []; //表格数据
  @Provide() page:number =1; // 当前page
  @Provide() size:number =5; // 请求数据的个数,默认5
  @Provide() total:number =0; //总数居的条数

  created(){
    this.loadData();
  }
  loadData(){
    (this as any).$axios(`/api/profiles/loadMore/${this.page}/${this.size}`)
    .then((res:any)=>{
      console.log(res.data);
    })
  }
}
</script>

<style>

</style>