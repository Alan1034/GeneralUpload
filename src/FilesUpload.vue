<!--
 * @Author: 陈德立*******419287484@qq.com
 * @Date: 2021-07-27 18:27:35
 * @LastEditTime: 2021-09-07 19:25:46
 * @LastEditors: 陈德立*******419287484@qq.com
 * @Github: https://github.com/Alan1034
 * @Description: 
 * @FilePath: \GeneralUpload\src\FilesUpload.vue
 * 
-->

<template>
  <ElUpload
    class="upload-demo"
    action="//"
    :on-preview="handlePreview"
    :on-remove="handleRemove"
    :before-remove="beforeRemove"
    multiple
    :on-exceed="handleExceed"
    :file-list="fileList"
    :before-upload="beforeUpload"
    v-bind="$attrs"
  >
    <ElButton size="small" type="primary" :disabled="loading"
      >点击上传</ElButton
    >
    <!-- <template #tip>
            <div class="el-upload__tip">
              只能上传 jpg/png 文件，且不超过 500kb
            </div>
          </template> -->
  </ElUpload>
</template>

<script>
import "element-plus/lib/theme-chalk/index.css";
import { ElButton, ElUpload, ElMessage, ElMessageBox } from "element-plus";

export default {
  name: "FilesUpload",
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
    beforeRemove(file, fileList) {
      if (!file) {
        return false;
      }
      return ElMessageBox.confirm(`确定移除 ${file.name}？`);
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

<style scoped>
::v-deep(.el-upload-list__item-name) {
  max-width: 250px;
}
::v-deep(.el-icon-close-tip) {
  display: none !important;
}
</style>
