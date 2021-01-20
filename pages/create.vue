<template>
  <b-container id="app">
    <b-card-body>
  <div class="Form-group">
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Question:"
        label-for="input-1"
      >
        <b-form-input
          class="col-md-12"
          id="input-1"
          v-model="form.question"
          type="question"
          placeholder="Enter Question"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group label="Chose Your image:">
      <div class="row">
        <div class="time col-md-4">
          <NumberInputSpinner
            :min="0"
            :max="90"
            :step="10"
            :integerOnly="true"
            v-model="time"
          />
        </div>

        <div class="col-md-8">
          <picture-input
            ref="pictureInput"
            @change="onChange"
            width="600"
            height="300"
            margin="16"
            accept="image/jpeg,image/png"
            size="10"
            :removable="true"
            :customStrings="{
        upload: '<h1>Bummer!</h1>',
        drag: 'Drag a 😺 GIF or GTFO'
      }">
          </picture-input>
        </div>
      </div>

      </b-form-group>
      <br>
      <b-form-group id="input-group-4" label="Select your correct answer:" v-slot="{ ariaDescribedby }">
        <b-form-checkbox-group
          v-model="form.checked"
          id="checkboxes-4"

          :aria-describedby="ariaDescribedby"
        >
          <b-form-checkbox value="true">true</b-form-checkbox>
          <b-form-checkbox value="false">false</b-form-checkbox>
        </b-form-checkbox-group>
      </b-form-group>

      <b-btn type="submit" variant="primary">Submit</b-btn>
      <b-alert variant="success">
        You clicked the button!
      </b-alert>
      <b-btn type="reset" variant="danger">Clear</b-btn>
    </b-form>
  </div>
    </b-card-body>
  </b-container>
</template>

<script>
  import PictureInput from 'vue-picture-input'
  import NumberInputSpinner from 'vue-number-input-spinner'

  export default {
    data() {
      return {
        arrayOfObjects: [],
        object: {
          name: 'Object Name',
        },
        form: {
          question: '',
          image: '',
          time:'',
          checked: []
        },
        show: true
      }
    },

    components: {
      PictureInput,
      NumberInputSpinner,
      // dropdown, // add new
    },
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
      add: function(inc){
        this.number +=inc;
      },
      subtract: function(dec){
        this.number -=dec;
      },
      methodToRunOnSelect(payload) {
        this.object = payload;
      },

      onChange () {
        console.log('New picture selected!')
        if (this.$refs.pictureInput.image) {
          console.log('Picture loaded.')
        } else {
          console.log('FileReader API not supported: use the <form>, Luke!')
        }
      }
    }
  }
</script>
<style scoped>

  .container {
    padding: 5% 10%;
    font-family: Serif,sans-serif;
    font-size: 17px;
    font-weight: bold;
  }
  .card-body {
    background-color: #F5F5F5;
    padding: 35px 35px;
  }
  .form-group {
  /*padding: 0 px 5px 15px 20px;*/
  }
  .picture-input{
    /*padding-left: 37%;*/
  }
  .time{
    width: 50px;
  }
  .timer{
    margin-top: 150px;
  }
  .col-md-4{
    padding-top: 100px;
    width: 50px;
  }

</style>
