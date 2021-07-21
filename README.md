# GeneralUpload

一个图片上传组件 <br/>
示例 <GeneralUpload
          :incomeForm="baseForm"
          prop="bsImage"
          :uploadPromise="uploadImage"
        />

数据示例:

baseForm: 传入一个 el-form 绑定的 Object

prop:绑定的 Object 中存放图片的字段

uploadPromise:上传图片的 Promise 函数，目前支持的返回格式为
{"code":200,"msg":null,"data":"http://test-public.oss-cn-beijing.aliyuncs.com/material/0079W9ghly1fwcmschqnwj30bc08y7a1.jpg"}

安装：npm i general-upload<br/>
install: npm i general-upload
