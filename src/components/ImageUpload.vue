<template>
  <div>
    <input type="file" required @change="onFileSelected" />
    <v-btn @click="onUpload">image upload</v-btn>
  </div>
</template>

<script>
export default {
  name: "ImageUpload",
  data() {
    return {
      image: '',
      link: ''
    };
  },
  methods: {
    // file을 선택하면 그 파일의 정보를 가져와 image에 정보를 넣어줌
    onFileSelected(event) {
      this.image = event.target.files[0];

      console.log("파일 선택 완료!",this.image);
    },

    onUpload() {
      console.log("이미지 업로드를 시작해보자");
      var form = new FormData();
      console.log(this.image)
      form.append("image", this.image);
      console.log(form)
      console.log(form.has('image'))
      // upload할 내용을 settings로
      var options = {
        method: "POST",
        headers: {
          Authorization: "Client-ID afdb9fa37087a4f",
        },
        body: form
      };

      fetch("https://api.imgur.com/3/image", options)
        .then(response => response.json())
        .then(result =>{
          if(result.success){
            this.link = result.data.link;
            console.log(this.link)

          }
          else{
            console.log("ERROR!!")
          }
        });

    }
  }
};
</script>
