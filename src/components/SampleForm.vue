<template>
  <div>
    <b-container>
      <validation-observer v-slot="{ invalid }">
        <b-form>
          <validation-provider
            v-slot="{ errors, valid }"
            name="Name"
            rules="required|max:20"
          >
            <b-form-group label="Name: ">
              <b-form-input
                v-model="name"
                placeholder="Enter Name"
                required
                type="text"
              ></b-form-input>
              <b-form-invalid-feedback :state="valid">
                <span
                  v-for="(error, index) in errors"
                  :key="index"
                >{{ error }}</span
                >
              </b-form-invalid-feedback>
            </b-form-group>
          </validation-provider>
          <validation-provider
            v-slot="{ errors, valid }"
            name="Email"
            rules="required|email"
          >
            <b-form-group label="Email address:">
              <b-form-input
                placeholder="Enter email"
                v-model="email"
                required
                type="email"
              ></b-form-input>
              <b-form-invalid-feedback :state="valid">
                <span
                  v-for="(error, index) in errors"
                  :key="index"
                >{{ error }}</span
                >
              </b-form-invalid-feedback>
            </b-form-group>
          </validation-provider>
          <validation-provider
            v-slot="{ errors, valid }"
            name="Phone Number"
            :rules="{required: true, phoneNumber: /^(01)([0-9]{9})$/ }"
          >
            <b-form-group label="Phone Number:">
              <b-form-input
                placeholder="Enter Phone Number"
                v-model="phone"
                required
                type="text"
              ></b-form-input>
              <b-form-invalid-feedback :state="valid">
                <span
                  v-for="(error, index) in errors"
                  :key="index"
                >{{ error }}</span
                >
              </b-form-invalid-feedback>
            </b-form-group>
          </validation-provider>
          <b-button variant="success" :disabled="invalid">Submit</b-button>
        </b-form>
      </validation-observer>
    </b-container>
  </div>
</template>

<script lang="ts">

import { Component, Vue } from 'vue-property-decorator'

import { extend, setInteractionMode, ValidationProvider, ValidationObserver } from 'vee-validate'
import { required, max, email, regex as phoneNumber } from 'vee-validate/dist/rules'

setInteractionMode('eager')

extend('required', {
  ...required,
  message: 'You may not left {_field_} empty'
})

extend('max', {
  ...max,
  message: '{_field_} should not exceed {length} characters'
})

extend('email', {
  ...email,
  message: '{_value_} is not a valid email'
})

extend('phoneNumber', {
  ...phoneNumber,
  message: 'Please enter a valid phone number'
})

@Component({ components: { ValidationProvider, ValidationObserver } })
export default class SampleForm extends Vue {
  private name = ''
  private email = ''
  private phone = ''
}
</script>
