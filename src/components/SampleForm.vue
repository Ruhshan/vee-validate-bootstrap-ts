<template>
  <div>
    <b-container>
      <b-form>
        <b-form-group
          label="Name: "
        >
          <b-form-input
            type="text"
            placeholder="Enter Name"
            required
          ></b-form-input>
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

@Component({ components: {} })
export default class SampleForm extends Vue {
}

</script>
