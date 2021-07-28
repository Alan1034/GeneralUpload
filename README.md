# GeneralUpload

##一个图片上传组件，有缩略图 <br/>
示例 <GeneralUpload
       :incomeForm="baseForm"
       prop="bsImage"
       :uploadFunction="uploadFunction"
     />

数据示例:

baseForm: 传入一个 el-form 绑定的 Object

prop:绑定的 Object 中存放图片的字段

uploadFunction:上传图片的函数，会返回一个 file 和传入的 prop;
uploadFunction(file, prop)

##一个多文件上传组件<br/>
示例 <FilesUpload
          prop="patternPath"
          :limit="3"
          :uploadFunction="uploadFunction"
          :removeFunction="removeFunction"
          :fileList="fileList"
        />

数据示例:

prop:绑定的 Object 中存放图片的字段

limit:设定能上传的最大数量

uploadFunction:上传图片的函数，会返回一个 file 和传入的 prop;
uploadFunction(file, prop)

removeFunction:删除图片后触发的函数，一般用来修改 fileList，会返回一个 file 和 fileList 和传入的 prop;
removeFunction(file, fileList, prop)

fileList:存放在 data 中的文件列表;
fileList: [{name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}, {name: 'food2.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}]

安装：npm i general-upload<br/>
install: npm i general-upload

使用：import { GeneralUpload, FilesUpload } from "general-upload";
