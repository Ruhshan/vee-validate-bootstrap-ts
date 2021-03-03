<template>
  <div>
    <b-container>
      <b-form>
        <b-form-group
          label="Name: "
        >
          <validation-provider rules="required" v-slot="{ errors, valid }" name="Name">
            <b-form-input
              type="text"
              v-model="name"
              placeholder="Enter Name"
              required
            ></b-form-input>
            <b-form-invalid-feedback :state="valid">
              <span v-for="error in errors" v-bind:key="error">{{ error }}</span>
            </b-form-invalid-feedback>
          </validation-provider>
        </b-form-group>
        <b-form-group
          label="Email address:"
        >
          <b-form-input
            type="email"
            placeholder="Enter email"
            required
          ></b-form-input>
        </b-form-group>
        <b-form-group
          label="Phone Number:"
        >
          <b-form-input
            type="text"
            placeholder="Enter Phone Number"
            required
          ></b-form-input>
        </b-form-group>
      </b-form>
      <b-button variant="success">Submit</b-button>
    </b-container>
  </div>
</template>

<script lang="ts">

import { Component, Vue } from 'vue-property-decorator'

import { extend, setInteractionMode, ValidationProvider } from 'vee-validate'
import { required } from 'vee-validate/dist/rules'

setInteractionMode('eager')

extend('required', {
  ...required,
  message: '{_field_} can not be empty'
})

@Component({ components: { ValidationProvider } })
export default class SampleForm extends Vue {
  private name = ''
}

</script>
