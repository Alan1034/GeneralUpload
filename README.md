# GeneralUpload

##一个图片上传组件，有缩略图 <br/>
示例：

      <GeneralUpload
       :incomeForm="baseForm"
       prop="bsImage"
       :uploadFunction="uploadFunction"
      />

![image-20210823115641161](https://raw.githubusercontent.com/Alan1034/PicturesServer/main/PicGo_imgs/image-20210823115641161.png?token=AICSKHQO7Z4QAFDPPZEH2GTBEMOLK)

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

![image-20210823120121891](https://raw.githubusercontent.com/Alan1034/PicturesServer/main/PicGo_imgs/image-20210823120121891.png?token=AICSKHU7LVIZKFBHUJOI26TBEMO44)

数据示例:

prop:绑定的 Object 中存放图片的字段

limit 和其他 Upload 组件的 Attribute(https://element-plus.org/#/zh-CN/component/upload):选传

uploadFunction:上传图片的函数，会返回一个 file 和传入的 prop，如果返回 false 或者返回 Promise 且被 reject,则停止上传;
uploadFunction(file, prop)

removeFunction:删除图片后触发的函数，一般用来修改 fileList，会返回一个 file 和 fileList 和传入的 prop;
removeFunction(file, fileList, prop)

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

![image-20210823120157995](https://raw.githubusercontent.com/Alan1034/PicturesServer/main/PicGo_imgs/image-20210823120157995.png?token=AICSKHRM6D4KZ6PP5BBUTZDBEMO7G)

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
