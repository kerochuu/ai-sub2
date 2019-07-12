<template>
  <div>
    <input type="file" required @change="onFileSelected" />
    <v-btn @click="onUpload">image upload</v-btn>
  </div>
</template>

<script>
import FirebaseService from '@/services/FirebaseService'

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
    },

    onUpload() {
      var form = new FormData();
      form.append("image", this.image);

      // upload할 내용을 options에 
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
            FirebaseService.postImage(this.link);
            alert("파일이 성공적으로 업로드 되었습니다.");
            this.$router.push('/pass')
          }
          else{
            console.log(result)
            alert("ERROR!!")
          }
        })
        .catch(err => {
          console.log(err)
        });

    },

  }
};
</script>
