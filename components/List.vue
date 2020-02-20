<template>
  <v-container>
    <v-card
      class="mx-auto mb-5 pa-0"
      outlined
      max-width="1450"
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="mb-1 pa-auto">
            {{ name }}
          </v-list-item-title>
          <v-col cols="10" />
        </v-list-item-content>
        <v-menu>
          <template v-slot:activator="{ on }">
            <v-btn
              class="cogs"
              icon
              v-on="on"
            >
              <v-icon>mdi-cogs</v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item @click="edit({id, name, description})">
              <v-list-item-title>Edit</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </v-list-item>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'ListContainer',
  props: {
    name: {
      type: String
    },
    id: {
      type: String
    },
    description: {
      type: String
    }
  },
  methods: {
    edit ({ id, name, description }) {
      this.$emit('edit', { id, name, description })
    }
  }
}
</script>

<style lang="scss" scoped>
  .v-card {
    left: 0;
    margin-left: 40px !important;
  }

  .cogs {
    position: absolute;
    top: 2%;
    right: 0.5%;
  }
</style>
