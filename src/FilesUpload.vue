/** 通用上传组件 使用方法：*/
<template>
  <ElUpload
    class="upload-demo"
    :on-preview="handlePreview"
    :on-remove="handleRemove"
    :before-remove="beforeRemove"
    multiple
    :limit="limit"
    :on-exceed="handleExceed"
    :file-list="fileList"
    :before-upload="beforeUpload"
    v-bind="$attrs"
  >
    <ElButton size="small" type="primary">点击上传</ElButton>
    <!-- <template #tip>
            <div class="el-upload__tip">
              只能上传 jpg/png 文件，且不超过 500kb
            </div>
          </template> -->
  </ElUpload>
</template>

<script>
import "element-plus/lib/theme-chalk/index.css";
import { ElButton, ElUpload,ElMessage,ElMessageBox } from "element-plus";

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
    limit: {
      type: Number,
      default: 3,
    },
    fileList: {
      type: Array,
      default: [],
    },
  },
  data() {
    return {

    };
  },
  methods: {
    handleRemove(file, fileList) {
      this.removeFunction(file, fileList)
    },
    handlePreview(file) {
      console.log(file);
    },
    handleExceed(files, fileList) {
      ElMessage.warning(
        `当前限制选择 3 个文件，本次选择了 ${files.length} 个文件，共选择了 ${
          files.length + fileList.length
        } 个文件`
      );
    },
    beforeRemove(file, fileList) {
      return ElMessageBox.confirm(`确定移除 ${file.name}？`);
    },
    async beforeUpload(file) {
      this.loading = true;
      const res = await this.uploadFunction(file, this.prop);
      this.loading = false;
    },
  },
};
</script>

<style></style>
