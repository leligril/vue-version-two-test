<template>
  <el-upload
    class="upload-demo"
    action="/upload"
    list-type="picture-card"
    :on-preview="handlePictureCardPreview"
    :on-remove="handleRemove"
    :file-list="fileList">
    <i slot="default" class="el-icon-plus"></i>
      <div slot="file" slot-scope="{ file }">
        <template v-if="file.type == 'video'">
          <video controls width="100%" height="100%">
            <source :src="file.url" type="video/mp4" />
          </video>
        </template>
        <template v-if="file.type == 'image'">
          <img class="el-upload-list__item-thumbnail" :src="file.url" alt="" />
        </template>

        <span class="el-upload-list__item-actions">
          <span
            class="el-upload-list__item-preview"
            @click="handlePictureCardPreview(file)"
          >
            <i class="el-icon-zoom-in"></i>
          </span>

          <span class="el-upload-list__item-delete" @click="handleRemove(file)">
            <i class="el-icon-delete"></i>
          </span>
        </span>
      </div>
  </el-upload>
</template>

<script>
export default {
  data() {
    return {
      fileList: [
        {type: "video", name: 'food.jpg', url: '../assets/20231208_225737.mp4' },
        {type: "image", name: 'nature.jpg', url: '../assets/logo.png' }
      ]
    };
  },
  methods: {
    handlePictureCardPreview(file) {
      // 自定义预览图片的操作
      console.log('预览图片', file);
    },
    handleRemove(file, fileList) {
      // 自定义移除文件的操作
      console.log('移除文件', file, fileList);
    }
  }
};
</script>

<style>

</style>
