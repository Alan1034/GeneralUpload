<!--
 * @Author: 陈德立*******419287484@qq.com
 * @Date: 2021-07-27 18:27:35
 * @LastEditTime: 2021-07-30 14:40:24
 * @LastEditors: 陈德立*******419287484@qq.com
 * @Github: https://github.com/Alan1034
 * @Description: 
 * @FilePath: \GeneralUpload\src\PicturesUpload.vue
 * 
-->

<template>
  <ElUpload
    class="upload-demo"
    action="//"
    :before-upload="beforeUpload"
    :on-preview="handlePreview"
    :on-remove="handleRemove"
    :file-list="fileList"
    multiple
    :on-exceed="handleExceed"
    :before-remove="beforeRemove"
    list-type="picture"
    v-bind="$attrs"
  >
    <div class="avatar-uploader">
      <span>
        <div class="icon-box">
          <i class="el-icon-plus avatar-uploader-icon"></i>
        </div>
        上传照片
      </span>
    </div>
  </ElUpload>
</template>

<script>
import "element-plus/lib/theme-chalk/index.css";
import { ElButton, ElUpload, ElMessage, ElMessageBox } from "element-plus";

export default {
  name: "PicturesUpload",
  components: {
    ElUpload,
    ElButton,
  },
  props: {
    prop: {
      type: String,
      default: "",
    },
    uploadFunction: {
      type: Function,
      default: () => {},
    },
    removeFunction: {
      type: Function,
      default: () => {},
    },
    fileList: {
      type: Array,
      default: [],
    },
  },
  data() {
    return { loading: false };
  },
  methods: {
    handleRemove(file, fileList) {
      this.removeFunction(file, fileList, this.prop);
    },
    beforeRemove(file, fileList) {
      if (!file) {
        return false;
      }
      return ElMessageBox.confirm(`确定移除 ${file.name}？`);
    },
    handlePreview(file) {
      ElMessage(file.name);
    },
    handleExceed(files, fileList) {
      ElMessage.warning(
        `当前限制选择 ${this.$attrs.limit} 个文件，本次选择了 ${
          files.length
        } 个文件，共选择了 ${files.length + fileList.length} 个文件`
      );
    },
    async beforeUpload(file) {
      this.loading = true;
      const res = await this.uploadFunction(file, this.prop);
      this.loading = false;
      return res;
    },
  },
};
</script>

<style lang="scss" scoped>
.avatar-uploader {
  border: 1px dashed #d9d9d9;
  border-radius: 6px;
  cursor: pointer;
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
