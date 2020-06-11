<template>
  <v-stepper v-model="step">
    <v-stepper-header>
      <v-stepper-step :complete="step > 1" step="1">Step 1: email info</v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step :complete="step > 2" step="2">Step 2: other emails</v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step step="3">Step 3: email text</v-stepper-step>
    </v-stepper-header>

    <v-stepper-items>
      <v-stepper-content step="1">
        <v-form ref="form" v-model="valid" lazy-validation>
          <h2> Alert on Email Wizard </h2>
          <p>Add a main email address.</p>
          <v-text-field
            v-model="name"
            :rules="nameRules"
            :counter="10"
            label="Name"
            required
          ></v-text-field>
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required />
          <v-select
            v-model="select"
            :items="items"
            :rules="[v => !!v || 'Hazard is required']"
            label="Hazards list:"
            required />
          <v-checkbox
            v-model="checkbox"
            :rules="[v => !!v || 'You must agree to continue!']"
            label="Do you agree?"
            required/>

          <v-btn :disabled="!valid"
            @click="submit">
            continue
          </v-btn>
          <v-btn @click.native="clear">clear</v-btn>
        </v-form>
      </v-stepper-content>

      <v-stepper-content step="2">
        <v-form>
          <h2> Other emails </h2>
          <p>Add other 4 email addresses.</p>
          <v-container>
            <v-layout flex wrap row>
              <v-flex d-flex lg6>
                <v-text-field
                  v-model="email1"
                  label="email 1" />
              </v-flex>
              <v-flex d-flex lg6>
                <v-text-field
                  v-model="email2"
                  label="email 2" />
              </v-flex>
              <v-flex d-flex lg6>
                <v-text-field
                  v-model="email3"
                  label="email 3" />
              </v-flex>
              <v-flex d-flex lg6>
                <v-text-field
                  v-model="email4"
                  label="email 4" />
              </v-flex>
              <v-flex d-flex lg2></v-flex>
              <v-flex d-flex lg4>
                <v-btn @click="step=3">
                  continue
                </v-btn>
              </v-flex>
              <v-flex d-flex lg4>
                <v-btn @click="step=1">clear</v-btn>
              </v-flex>
            </v-layout>
          </v-container>
        </v-form>
      </v-stepper-content>

      <v-stepper-content step="3">
        <h2> Add info into body of email </h2>
          <v-textarea
            value ="Nostrud exercitation commodo consequat.Nostrud exercitation commodo consequat.Nostrud exercitation commodo consequat.Nostrud exercitation commodo consequat.
            Nostrud exercitation commodo consequat.Nostrud exercitation commodo consequat.Nostrud exercitation commodo consequat.Nostrud exercitation commodo consequat.
            Nostrud exercitation commodo consequat.Nostrud exercitation commodo consequat.Nostrud exercitation commodo consequat.Nostrud exercitation commodo consequat."
            :auto-grow="autoGrow"
            :clearable="clearable"
            :counter="counter ? counter : false"
            :filled="filled"
            :flat="flat"
            :hint="hint"
            :label="label"
            :loading="loading"
            :no-resize="noResize"
            :outlined="outlined"
            :persistent-hint="persistentHint"
            :placeholder="placeholder"
            :rounded="rounded"
            :row-height="rowHeight"
            :rows="rows"
            :shaped="shaped"
            :single-line="singleLine"
            :solo="solo"
          ></v-textarea>
        <v-checkbox label="Are you sure to sent to all ?"></v-checkbox>

        <v-btn @click="step=1">continue</v-btn>
      </v-stepper-content>
    </v-stepper-items>
  </v-stepper>
</template>

<script>
  export default {
    data () {
      return {
        step: 0,
        valid: true,
        name: '',
        nameRules: [
          v => !!v || 'Name is required',
          v => (v && v.length <= 10) || 'Name must be less than 10 characters'
        ],
        email: '',
        emailRules: [
          v => !!v || 'E-mail is required',
          v => /.+@.+/.test(v) || 'E-mail must be valid'
        ],
        select: null,
        items: [
          'S-a spart o teava',
          'Broasca stricata la usa de la intrare',
          'Probleme cu aerul conditionat',
          'Sistem prost de ventialtie la et. 3'
        ],
        checkbox: false,
        date: new Date().toISOString().substr(0, 10)
      }
    },

    methods: {
      submit () {
        if (this.$refs.form.validate()) {

        }

        this.step = 2;
      },
      clear () {
        this.$refs.form.reset()
      }
    }
  }
</script>

<style>
</style>
