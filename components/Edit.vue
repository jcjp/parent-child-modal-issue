<template>
  <v-container>
    <Modal
      :value="value"
      @input="$emit('input', arguments[0])"
    >
      <v-card class="pa-10">
        <v-card-text>
          <h1>
            Edit {{ nameProps }}
          </h1>
        </v-card-text>
        <v-form
          id="edit-category-modal-form"
          ref="form"
          v-model="valid"
        >
          <v-text-field
            ref="name"
            v-model="name"
            label="Name"
            filled
            placeholder="e.g. Category Title Example"
            required
          />

          <v-text-field
            ref="description"
            v-model="description"
            label="Description"
            filled
            placeholder="This is a sample description"
            required
          />

          <v-card-actions id="edit-category-modal-actions">
            <v-btn
              text
              @click.prevent="closeModal"
            >
              Cancel
            </v-btn>
            <v-btn
              :disabled="!valid"
              color="indigo"
              text
              absolute
              right
              @click.prevent="updateCategory({name, descriptionProps})"
            >
              Edit category
            </v-btn>
          </v-card-actions>
        </v-form>
      </v-card>
    </Modal>
  </v-container>
</template>

<script>
import Modal from '~/components/Modal.vue'

export default {
  name: 'EditModal',
  components: { Modal },
  props: {
    id: {
      type: String
    },
    nameProps: {
      type: String
    },
    descriptionProps: {
      type: String
    },
    value: {
      type: Boolean,
      required: true,
      default: false
    }
  },
  data () {
    return {
      valid: false,
      name: '',
      originalName: '',
      description: '',
      originalDescription: ''
    }
  },
  methods: {
    updateCategory ({ name, descriptionProps }) {
      this.valid = false
      this.closeModal()
    },
    closeModal () {
      this.valid = true
      this.$emit('input', false)
    }
  }
}
</script>
