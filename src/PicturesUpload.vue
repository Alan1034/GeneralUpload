<!--
 * @Author: 陈德立*******419287484@qq.com
 * @Date: 2021-07-27 18:27:35
 * @LastEditTime: 2024-10-09 17:49:39
 * @LastEditors: 陈德立*******419287484@qq.com
 * @Github: https://github.com/Alan1034
 * @Description: 
 * @FilePath: \GeneralUpload\src\PicturesUpload.vue
 * 
-->

<template>
  <el-upload class="upload-demo" action="//" :before-upload="beforeUpload" :on-preview="handlePreview"
    :on-remove="handleRemove" :file-list="fileList" multiple :on-exceed="handleExceed" :before-remove="beforeRemove"
    :list-type="listType" v-bind="$attrs">
    <div :class="innerClassName">
      <span class="avatar-uploader-box">
        <div class="icon-box">
          <i class="el-icon-plus avatar-uploader-icon"></i>
        </div>
        {{ prompt || "上传照片" }}
      </span>
    </div>
  </el-upload>
</template>

<script>
export default {
  name: "PicturesUpload",
  props: {
    uploadFunction: {
      type: Function,
      default: () => { },
    },
    removeFunction: {
      type: Function,
      default: () => { },
    },
    previewFunction: {
      type: Function,
      default: () => { },
    },
    exceedFunction: {
      type: Function,
      default: () => { },
    },
    fileList: {
      type: Array,
      default: [],
    },
    prompt: {
      type: String,
      default: "",
    },
    listType: {
      type: String,
      default: "picture",
    }
  },
  data() {
    return { loading: false };
  },
  computed: {
    innerClassName() {
      let className = ''
      switch (this.listType) {
        case "picture":
          className = 'avatar-uploader'
          break;
        case "picture-card":
          className = 'avatar-card-uploader'
          break;

        default:
          break;
      }
      return className
    },
  },
  methods: {
    handleRemove(file, fileList) {
      this.removeFunction(file, fileList);
    },
    beforeRemove(file, fileList) {
      if (!file) {
        return false;
      }
      return this.$confirm(`确定移除 ${file.name}？`);
    },
    handlePreview(file) {
      this.$message(file.name);
      this.previewFunction(file);
    },
    handleExceed(files, fileList) {
      this.$message.warning(
        `当前限制选择 ${this.$attrs.limit} 个文件，本次选择了 ${files.length
        } 个文件，共选择了 ${files.length + fileList.length} 个文件`
      );
      this.exceedFunction(files, fileList);
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

.avatar-card-uploader {
  border: 1px dashed #d9d9d9;
  border-radius: 6px;
  cursor: pointer;
  overflow: hidden;
  height: 100%;
  width: 100%;
  background-color: #f5f7fa;

  .avatar-uploader-box {
    display: flex;
    justify-content: center;
    align-items: center;

    .icon-box {
      display: grid;
    }
  }

  img {
    max-width: 100%;
    max-height: 100%;
  }
}
</style>
