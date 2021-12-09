<template>
  <div class="nx-data-display">
    <el-row :span="24">
      <el-col v-for="(item,index) in data" :key="index" :span="span">
        <div class="item" :style="{color:color,border:'1px solid #ccc',marginRight:'10px'}">
          <h5 class="count"><nx-count-up ref="count" :start="14" :end="item.count" :duration="item.duration" /></h5>
          <span class="splitLine" />
          <p class="title">{{ item.title }}</p>
          <!-- <el-button primry="danger" @click="pause(index)">stop </el-button> -->
        </div>
      </el-col>
    </el-row>

  </div>
</template>

<script>
import nxCountUp from '@/components/nx-count-up/index.vue'
export default {
  name: 'NxDataDisplay',
  components: {
    nxCountUp
  },
  props: {
    option: {
      type: Object,
      default: () => {}
    }
  },
  data() {
    return {
      span: this.option.span || 8,
      data: this.option.data,
      color: this.option.color || 'rgb(63, 161, 255)'
    }
  },
  created() {},
  methods: {
    pause(i) {
      this.$refs['count'][i].pauseResume()
    }
  }
}
</script>
