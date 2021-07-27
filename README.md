# GeneralUpload

一个图片上传组件 <br/>
示例 <GeneralUpload
       :incomeForm="baseForm"
       prop="bsImage"
       :uploadFunction="uploadFunction"
     />

数据示例:

baseForm: 传入一个 el-form 绑定的 Object

prop:绑定的 Object 中存放图片的字段

uploadFunction:上传图片的函数，会返回一个file和传入的prop

安装：npm i general-upload<br/>
install: npm i general-upload

使用：import { GeneralUpload, FilesUpload } from "general-upload";