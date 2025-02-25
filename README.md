<!-- @format -->

# GeneralUpload

##一个图片上传组件，有缩略图，vue2请使用@1版本，Vue3请使用@2版本<br/>
示例：

      <GeneralUpload
       :incomeForm="baseForm"
       prop="bsImage"
       :uploadFunction="uploadFunction"
      />

![img](https://raw.githubusercontent.com/Alan1034/PicturesServer/main/PicGo_imgs/202108231135353.png)

数据示例:

baseForm: 传入一个 el-form 绑定的 Object

prompt:上传组件上显示的文字

prop:绑定的 Object 中存放图片的字段

uploadFunction:上传图片的函数，会返回一个 file 和传入的 prop，如果返回 false 或者返回 Promise 且被 reject,则停止上传;
uploadFunction(file, prop)

其他 Upload 组件的 Attribute(https://element.eleme.io/#/zh-CN/component/upload) :选传

# FilesUpload

##一个多文件上传组件<br/>
示例：

         <FilesUpload
          prop="patternPath"
          :limit="3"
          :uploadFunction="uploadFunction"
          :removeFunction="removeFunction"
          :fileList="fileList"
        />
        
         <FilesUpload
          onlyList 
          :previewFunction="handlePreview" 
          :fileList="fileList"
        />
        
          <FilesUpload :uploadFunction="uploadFunction" :removeFunction="removeFunction" :previewFunction="previewFunction"
            pure multiple :limit="5" accept="image/png,application/pdf,image/jpeg" :fileList="fileList">
            <template v-slot:trigger>
              <el-button class="upload-button">选择文件</el-button>
            </template>
            <template v-slot:tip>
              <span class="slot-tip">
                支持上传不超过5个文档，可支持上传pdf、jpg、png等文件格式
              </span>
            </template>
          </FilesUpload>

![img](https://raw.githubusercontent.com/Alan1034/PicturesServer/main/PicGo_imgs/202108231137554.png)

数据示例:

onlyList:是否纯展示

pure:不展示点击上传按钮，可以改为slot传入

prompt:上传按钮上显示的文字

limit 和其他 Upload 组件的 Attribute(https://element.eleme.io/#/zh-CN/component/upload):选传

uploadFunction:上传图片的函数，会返回一个 file 和传入的 prop，如果返回 false 或者返回 Promise 且被 reject,则停止上传;
uploadFunction(file)

removeFunction:删除图片后触发的函数，一般用来修改 fileList，会返回一个 file 和 fileList 和传入的 prop;
removeFunction(file, fileList)

previewFunction:点击附件后触发的函数，一般用来制作点击后预览/下载文件
previewFunction(file)

handleExceed:当超出限制时触发的函数
handleExceed(file)

fileList:存放在 data 中的文件列表;
fileList: [{name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}, {name: 'food2.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}]

# PicturesUpload

##一个多图片上传组件<br/>
示例:

        <PicturesUpload
          prop="itemImages"
          :uploadFunction="uploadFunction"
          :removeFunction="removeFunction"
          :fileList="fileList"
          :limit="5"
          accept="image/png,image/bmp,image/jpeg"
        />

![img](https://raw.githubusercontent.com/Alan1034/PicturesServer/main/PicGo_imgs/202108231137062.png)

数据示例:

prop:绑定的 Object 中存放图片的字段

prompt:上传组件上显示的文字

limit 和其他 Upload 组件的 Attribute(https://element.eleme.io/#/zh-CN/component/upload):选传

uploadFunction:上传图片的函数，会返回一个 file 和传入的 prop，如果返回 false 或者返回 Promise 且被 reject,则停止上传;
uploadFunction(file)

removeFunction:删除图片后触发的函数，一般用来修改 fileList，会返回一个 file 和 fileList 和传入的 prop;
removeFunction(file, fileList)

previewFunction:点击附件后触发的函数，一般用来制作点击后下载文件
previewFunction(file)

exceedFunction:当超出限制时触发的函数
exceedFunction(file)

fileList:存放在 data 中的文件列表;
fileList: [{name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}, {name: 'food2.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}]

accept:https://www.iana.org/assignments/media-types/media-types.xhtml#image

安装：npm i general-upload<br/>
install: npm i general-upload

使用：import { GeneralUpload, FilesUpload,PicturesUpload } from "general-upload";
import 'general-upload/style'