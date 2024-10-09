<!--
 * @Author: 陈德立*******419287484@qq.com
 * @Date: 2021-07-27 18:27:35
 * @LastEditTime: 2024-10-08 15:31:12
 * @LastEditors: 陈德立*******419287484@qq.com
 * @Github: https://github.com/Alan1034
 * @Description: 
 * @FilePath: \GeneralUpload\src\FilesUpload.vue
 * 
-->

<template>
  <el-upload
    class="upload-demo"
    action="//"
    :on-preview="handlePreview"
    :on-remove="handleRemove"
    :before-remove="beforeRemove"
    multiple
    :on-exceed="handleExceed"
    :file-list="fileList"
    :before-upload="beforeUpload"
    :disabled="onlyList"
    v-bind="$attrs"
  >
    <el-button :size="size" type="primary" :disabled="loading" v-if="!onlyList"
      >{{ prompt || "点击上传" }}</el-button
    >
    <!-- <template #tip>
            <div class="el-upload__tip">
              只能上传 jpg/png 文件，且不超过 500kb
            </div>
          </template> -->
  </el-upload>
</template>

<script>
export default {
  name: "FilesUpload",
  props: {
    onlyList: {
      type: Boolean,
      default: false,
    },
    size: {
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
    previewFunction: {
      type: Function,
      default: () => {},
    },
    exceedFunction: {
      type: Function,
      default: () => {},
    },
    fileList: {
      type: Array,
      default: [],
    },
    prompt: {
      type: String,
      default: "",
    },
  },
  data() {
    return { loading: false };
  },
  methods: {
    handleRemove(file, fileList) {
      this.removeFunction(file, fileList);
    },
    handlePreview(file) {
      this.$message(file.name);
      this.previewFunction(file);
    },
    handleExceed(files, fileList) {
      this.$message.warning(
        `当前限制选择 ${this.$attrs.limit} 个文件，本次选择了 ${
          files.length
        } 个文件，共选择了 ${files.length + fileList.length} 个文件`
      );
      this.exceedFunction(files, fileList);
    },
    beforeRemove(file, fileList) {
      if (!file) {
        return false;
      }
      return this.$confirm(`确定移除 ${file.name}？`);
    },
    async beforeUpload(file) {
      this.loading = true;
      const res = await this.uploadFunction(file);
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
