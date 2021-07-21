/** 通用上传组件 使用方法：
<GeneralUpload
  :incomeForm="baseForm"
  prop="bsImage"
  :uploadPromise="uploadImage"
/>
*/
<template>
  <ElUpload
    class="avatar-uploader"
    :before-upload="beforeUpload"
    :show-file-list="false"
    :on-success="handleAvatarSuccess"
  >
    <img v-if="incomeForm[prop]" :src="incomeForm[prop]" class="avatar" />
    <span v-else>
      <div class="icon-box">
        <i class="el-icon-loading avatar-uploader-icon" v-if="loading"></i>
        <i class="el-icon-plus avatar-uploader-icon" v-else></i>
      </div>
      上传照片
    </span>
  </ElUpload>
</template>

<script>
import "element-plus/lib/theme-chalk/index.css";
import { ElUpload } from "element-plus";

export default {
  name: "GeneralUpload",
  components: {
    ElUpload,
  },
  data() {
    return { loading: false };
  },
  props: {
    incomeForm: {
      type: Object,
      default: {},
    },
    prop: {
      type: String,
      default: "",
    },
    uploadPromise: {
      type: Function,
      default: () => {},
    },
  },
  watch: {
    incomeForm() {
      console.log(this.incomeForm[this.prop]);
    },
  },
  methods: {
    async beforeUpload(file) {
      this.loading = true;
      const formData = new FormData();
      formData.append("file", file);
      const res = await this.uploadPromise(formData);
      if (res.code === 200) {
        this.incomeForm[this.prop] = res.data;
      }
      this.loading = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.avatar-uploader {
  border: 1px dashed #d9d9d9;
  border-radius: 6px;
  cursor: pointer;
  display: flex;
  overflow: hidden;
  display: flex;
  width: 100px;
  height: 100px;
  justify-content: center;
  align-items: center;
  background-color: #f5f7fa;
  .icon-box {
    display: grid;
  }
  img {
    max-width: 100%;
    max-height: 100%;
  }
}
</style>
