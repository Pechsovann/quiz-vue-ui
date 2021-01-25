<template>
  <div id="app" class="container">
  <div class="Form-group">

    <!--    add new-->


    <div class="links">
      <a
        href="http://localhost:3000/create"
        target="_blank"
        rel="noopener noreferrer"
        class="button--green"
      >
        Add new
      </a>
    </div>
<!--add new end-->

    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Question:"
        label-for="input-1"
      >
        <b-form-input
          class="col-md-10"
          id="input-1"
          v-model="form.question"
          type="question"
          placeholder="Enter Question"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Chose Your image:">
      <div class="col-md-10">

        <div class="image">

        <div class="form-group" style="height: 150px; width: auto">
          <b-label for="files"></b-label>

          <span>
                  <b-form-group  style="width: 100%; height: 100%; font-size: 0px; border-image: 70% ; margin-bottom: 1rem; background-color: rgb(29, 161, 242); background-image: url(&quot;https://abs.twimg.com/a/1498195419/img/t1/highline/empty_state/owner_empty_avatar.png&quot;); background-position: 50% center;">
                     <!-- react-text: 85 -->Try dropping some files.<!-- /react-text --><input type="file" accept="image/jpeg, image/png" multiple="" style="display: none;">
                  </b-form-group>
                  <button type="button" class="btn btn-secondary btn-sm btn-block">Upload new Photo</button><!-- react-text: 88 --><!-- /react-text -->
          </span>
        </div>
        </div>
      </div>
      </b-form-group>

<!--      <picture-input-->
<!--        ref="pictureInput"-->
<!--        @change="onChange"-->
<!--        width="600"-->
<!--        height="600"-->
<!--        margin="16"-->
<!--        accept="image/jpeg,image/png"-->
<!--        size="10"-->
<!--        :removable="true"-->
<!--        :customStrings="{-->
<!--        upload: '<h1>Bummer!</h1>',-->
<!--        drag: 'Drag a 😺 GIF or GTFO'-->
<!--      }">-->
<!--      </picture-input>-->

      <br>
      <b-form-group id="input-group-4" label="Select your correct answer:" v-slot="{ ariaDescribedby }">
        <b-form-checkbox-group
          v-model="form.checked"
          id="checkboxes-4"

          :aria-describedby="ariaDescribedby"
        >
<!--          <b-form-checkbox value="true">true</b-form-checkbox>-->
<!--          <b-form-checkbox value="false">false</b-form-checkbox>-->

          <!--add new-->
          <div class="radio">
            <label>
              <input type="radio" class="option-input radio" name="example" checked />
              True
            </label>
            <label>
              <input type="radio" class="option-input radio" name="example" />
              false
            </label>
          </div>

<!--          radio end-->

        </b-form-checkbox-group>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Clear</b-button>
    </b-form>
  </div>
  </div>
</template>
import Router from 'vue-router';
import AddNew from '../pages/create.vue'
<script>
  export default {
    data() {
      return {
        form: {
          question: '',
          image: '',
          checked: []
        },

        // mime_type: '',
        // cropedImage: '',
        // autoCrop: false,
        // selectedFile: '',
        // image: '',
        // dialog: false,
        // files: '',

        show: true
      }
    },
    // components: {
    //   PictureInput
    // },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        alert(JSON.stringify(this.form))
      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.question = ''
        this.form.image = ''

        this.form.checked = []
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      },
      // add new
      //   saveImage() {
      //     const userId = this.$route.params.user_id
      //     this.cropedImage = this.$refs.cropper.getCroppedCanvas().toDataURL()
      //     this.$refs.cropper.getCroppedCanvas().toBlob((blob) => {
      //       const formData = new FormData()
      //       formData.append('profile_photo', blob, 'name.jpeg')
      //       axios
      //         .post('/api/user/' + userId + '/profile-photo', formData)
      //         .then((response) => {
      //         })
      //         .catch(function (error) {
      //           console.log(error)
      //         })
      //     }, this.mime_type)
      //   },
      //   onFileSelect(e) {
      //     const file = e.target.files[0]
      //     this.mime_type = file.type
      //     console.log(this.mime_type)
      //     if (typeof FileReader === 'function') {
      //       this.dialog = true
      //       const reader = new FileReader()
      //       reader.onload = (event) => {
      //         this.selectedFile = event.target.result
      //         this.$refs.cropper.replace(this.selectedFile)
      //       }
      //       reader.readAsDataURL(file)
      //     } else {
      //       alert('Sorry, FileReader API not supported')
      //     }
      //   },
      // },
    //   onChange () {
    //     console.log('New picture selected!')
    //     if (this.$refs.pictureInput.image) {
    //       console.log('Picture loaded.')
    //     } else {
    //       console.log('FileReader API not supported: use the <form>, Luke!')
    //     }
    //   }
    //
    }
  }
</script>
<style scoped>
  /*#app {*/
  /*  font-family: 'Avenir', Helvetica, Arial, sans-serif;*/
  /*  -webkit-font-smoothing: antialiased;*/
  /*  -moz-osx-font-smoothing: grayscale;*/
  /*  text-align: center;*/
  /*  color: #2c3e50;*/
  /*  margin-top: 60px;*/
  /*}*/
  .container {
    padding: 5% 20%;
  }
  .form-group {
  /*padding: 0 px 5px 15px 20px;*/
  }
  .image {
    padding-left: 40%;
  }

  /*add new*/
  .links{
    padding-left: 71%;
  }


  *{font-family: 'Roboto', sans-serif;}

  @keyframes click-wave {
    0% {
      height: 40px;
      width: 40px;
      opacity: 0.35;
      position: relative;
    }
    100% {
      height: 200px;
      width: 200px;
      margin-left: -80px;
      margin-top: -80px;
      opacity: 0;
    }
  }

  .option-input {
    -webkit-appearance: none;
    -moz-appearance: none;
    -ms-appearance: none;
    -o-appearance: none;
    appearance: none;
    position: relative;
    top: 13.33333px;
    right: 0;
    bottom: 0;
    left: 0;
    height: 40px;
    width: 40px;
    transition: all 0.15s ease-out 0s;
    background: #cbd1d8;
    border: none;
    color: #fff;
    cursor: pointer;
    display: inline-block;
    margin-right: 0.5rem;
    outline: none;
    position: relative;
    z-index: 1000;
  }
  .option-input:hover {
    background: #9faab7;
  }
  .option-input:checked {
    background: #40e0d0;
  }
  .option-input:checked::before {
    height: 30px;
    width: 30px;
    position: absolute;
    content: '✔';
    display: inline-block;
    font-size: 26.66667px;
    text-align: center;
    line-height: 40px;
  }
  .option-input:checked::after {
    -webkit-animation: click-wave 0.65s;
    -moz-animation: click-wave 0.65s;
    animation: click-wave 0.65s;
    background: #526488;
    content: '';
    display: block;
    position: relative;
    z-index: 100;
  }
  .option-input.radio {
    border-radius: 50%;
  }
  .option-input.radio::after {
    border-radius: 50%;
  }

  body {
    display: -webkit-box;
    display: -moz-box;
    display: -ms-flexbox;
    background: #e8ebee;
    color: #9faab7;
    font-family: "Helvetica Neue", "Helvetica", "Roboto", "Arial", sans-serif;
    text-align: center;
  }




</style>
