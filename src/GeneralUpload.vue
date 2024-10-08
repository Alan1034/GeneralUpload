<!--
 * @Author: 陈德立*******419287484@qq.com
 * @Date: 2021-07-21 18:01:00
 * @LastEditTime: 2024-03-13 15:58:58
 * @LastEditors: 陈德立*******419287484@qq.com
 * @Github: https://github.com/Alan1034
 * @Description: 
 * 通用上传组件 使用方法：
 * <GeneralUpload
 *  :incomeForm="baseForm"
 *  prop="bsImage"
 *  :uploadFunction="uploadFunction"
 * />
 *
 * @FilePath: \GeneralUpload\src\GeneralUpload.vue
 * 
-->

<template>
  <el-upload
    class="avatar-uploader"
    action="//"
    :before-upload="beforeUpload"
    :show-file-list="false"
    :disabled="loading"
    v-bind="$attrs"
  >
    <img v-if="incomeForm[prop]" :src="incomeForm[prop]" class="avatar" />
    <span v-else>
      <div class="icon-box">
        <i class="el-icon-loading avatar-uploader-icon" v-if="loading"></i>
        <i class="el-icon-plus avatar-uploader-icon" v-else></i>
      </div>
      {{ prompt || "上传照片" }}
    </span>
  </el-upload>
</template>

<script>

export default {
  name: "GeneralUpload",
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
    uploadFunction: {
      type: Function,
      default: () => {},
    },
    prompt: {
      type: String,
      default: "",
    },
  },
  // watch: {
  //   incomeForm() {
  //     console.log(this.incomeForm[this.prop]);
  //   },
  // },
  methods: {
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
