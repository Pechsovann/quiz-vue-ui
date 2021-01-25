<template>
    <b-container class="mt-5 ">
      <b-row >
        <b-card class="col-md-9" >
            <p style="text-align: center;font-size: 25px;font-family: 'Avenir', Helvetica, Arial, sans-serif;">Create quiz true & false</p>
            <b-card-body class="col-md-12">
              <b-form>
                <b-form-group>
                  <b-input type="text" v-model="form.question" aria-label="Question" placeholder="Question..."></b-input>
                </b-form-group>
                <b-input class="time" style="text-align: center" id="id_form-0-quantity" min="0" name="form-0-quantity" value="1" type="number"/>
                <b-button type="submit"  variant="primary">Submit</b-button>
              </b-form>
              <b-form class="time">
              <NumberInputSpinner
                :min="0"
                :max="90"
                :step="5"
                :integerOnly="true"
                v-model="timer"
              />

              </b-form>

            </b-card-body>

        </b-card>
      </b-row>
    </b-container>
</template>

<script>
  import NumberInputSpinner from 'vue-number-input-spinner'
    export default {
      name: "quiz",
      data() {
        return {
          form: {
            question: '',
            correctAnswer: '',
            image: '',
            timed: ''
          }
        }
      },
      methods: {
        onSubmit(event) {
          event.preventDefault()
          alert(JSON.stringify(this.form))
        },
      },
      components: {
        NumberInputSpinner,
      },
    }
</script>
<style scoped>

  button{
    margin-left: 91%;
  }
  .time {
    width: 140px;
  }


</style>
