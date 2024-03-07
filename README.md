# GeneralUpload

##一个图片上传组件，有缩略图 <br/>
示例：

      <GeneralUpload
       :incomeForm="baseForm"
       prop="bsImage"
       :uploadFunction="uploadFunction"
      />

![img](https://raw.githubusercontent.com/Alan1034/PicturesServer/main/PicGo_imgs/202108231135353.png?token=AICSKHVN6DVTLAX3RCTF4P3BEM6XQ)

数据示例:

baseForm: 传入一个 el-form 绑定的 Object

prop:绑定的 Object 中存放图片的字段

uploadFunction:上传图片的函数，会返回一个 file 和传入的 prop，如果返回 false 或者返回 Promise 且被 reject,则停止上传;
uploadFunction(file, prop)

其他 Upload 组件的 Attribute(https://element-plus.org/#/zh-CN/component/upload) :选传

##一个多文件上传组件<br/>
示例：

         <FilesUpload
          prop="patternPath"
          :limit="3"
          :uploadFunction="uploadFunction"
          :removeFunction="removeFunction"
          :fileList="fileList"
        />

![img](https://raw.githubusercontent.com/Alan1034/PicturesServer/main/PicGo_imgs/202108231137554.png?token=AICSKHUHZEIRTK5TMMDJSOLBEM67I)

数据示例:

onlyList:是否纯展示

limit 和其他 Upload 组件的 Attribute(https://element-plus.org/#/zh-CN/component/upload):选传

uploadFunction:上传图片的函数，会返回一个 file 和传入的 prop，如果返回 false 或者返回 Promise 且被 reject,则停止上传;
uploadFunction(file)

removeFunction:删除图片后触发的函数，一般用来修改 fileList，会返回一个 file 和 fileList 和传入的 prop;
removeFunction(file, fileList)

fileList:存放在 data 中的文件列表;
fileList: [{name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}, {name: 'food2.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}]

##一个多图片上传组件<br/>
示例:

        <PicturesUpload
          prop="itemImages"
          :uploadFunction="uploadFunction"
          :removeFunction="removeFunction"
          :fileList="fileList"
          :limit="5"
        />

![img](https://raw.githubusercontent.com/Alan1034/PicturesServer/main/PicGo_imgs/202108231137062.png?token=AICSKHXPKULI5RQ4LG4RHOTBEM65E)

数据示例:

prop:绑定的 Object 中存放图片的字段

limit 和其他 Upload 组件的 Attribute(https://element-plus.org/#/zh-CN/component/upload):选传

uploadFunction:上传图片的函数，会返回一个 file 和传入的 prop，如果返回 false 或者返回 Promise 且被 reject,则停止上传;
uploadFunction(file, prop)

removeFunction:删除图片后触发的函数，一般用来修改 fileList，会返回一个 file 和 fileList 和传入的 prop;
removeFunction(file, fileList, prop)

fileList:存放在 data 中的文件列表;
fileList: [{name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}, {name: 'food2.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}]

安装：npm i general-upload<br/>
install: npm i general-upload

使用：import { GeneralUpload, FilesUpload } from "general-upload";
import 'general-upload/style'
