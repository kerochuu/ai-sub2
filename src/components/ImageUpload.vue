<template>

    <v-layout>
        <v-flex>
            <label>
                <input outline type="file" id="file" ref="file" @change="handleFileUpload()"/>
            </label>
            <v-btn v-on:click="randomImageUpload()">
                Random Poster Image
            </v-btn>
            <div>
                <img id="preview" src=""
                     height="200px"
                     style="display: none"/>
            </div>
        </v-flex>
    </v-layout>
</template>

<script>
    import FirebaseService from '@/services/FirebaseService'

    export default {
        name: "ImageUpload",
        props: {
            img: {
                type: String,
                default: ""
            },
            randomImage: {
                type : Boolean,
                default: false
            }
        },
        components: {},
        data() {
            return {
                file: ''
            }
        },
        methods: {
            async imageUpload() {
                console.log(this.$refs.file.files.length)
                console.log(this.randomImage)
                if (this.$refs.file.files.length == 0 && this.randomImage == false) { // 파일 선택 취소 할 시 섬네일 안보임
                    document.getElementById('preview').style.display = "none";
                    alert("이미지를 업로드 해주세요.")
                    return;
                }
                if (this.randomImage) {
                    this.img = document.getElementById('preview').getAttribute('src');
                } else {
                    this.img = await FirebaseService.posterUpload(this.file)
                }
                 FirebaseService.postImage(this.img); ////////////////////////////////////////////////////
                console.log("이미지URL : " + this.img)
                return this.img;
            },
            handleFileUpload() {
                this.file = this.$refs.file.files[0]
                console.log(this.$refs.file.files.length)

                if (this.$refs.file.files.length == 0) { // 파일 선택 취소 할 시 섬네일 안보임
                    document.getElementById('preview').style.display = "none";
                    return;
                }

                let reader = new FileReader();
                reader.readAsDataURL(this.file);
                //로드 한 후
                reader.onload = function () {
                    //로컬 이미지를 보여주기
                    document.querySelector('#preview').src = reader.result;
                    document.getElementById('preview').style.display = "block"; // 섬네일 이미지 보임
                };
                this.randomImage = false;
            },
            randomImageUpload() {
                document.querySelector('#preview').src = "https://source.unsplash.com/random";
                document.getElementById('preview').style.display = "block"; // 섬네일 이미지 보임
                this.randomImage = true;
            }
        }
    };
</script>

<style scoped>

</style>
