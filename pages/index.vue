<template>
  <div>
    <ListComponent
      v-for="(d, index) in data"
      :id="d.id"
      :key="index"
      :name="d.name"
      :description="d.description"
      @edit="editData"
    />
    <EditComponent
      :id="selected.id"
      v-model="isOpenModal"
      :name="selected.name"
      :description="selected.description"
    />
  </div>
</template>
<script>
import ListComponent from '~/components/List.vue'
import EditComponent from '~/components/Edit.vue'

export default {
  components: {
    ListComponent,
    EditComponent
  },
  layout: 'default',
  data () {
    return {
      data: [],
      isOpenModal: false,
      selected: {
        id: '',
        name: '',
        description: ''
      }
    }
  },
  async mounted () {
    await this.getAllCategories()
  },
  methods: {
    async getAllCategories () {
      this.data = await new Promise((resolve) => {
        setTimeout(() => {
          resolve([
            {
              id: '1',
              name: 'category-1',
              description: 'description 1'
            },
            {
              id: '2',
              name: 'category-2',
              description: 'description 2'
            },
            {
              id: '3',
              name: 'category-3',
              description: 'description 3'
            },
            {
              id: '4',
              name: 'category-4',
              description: 'description 4'
            },
            {
              id: '5',
              name: 'category-5',
              description: 'description 5'
            }
          ])
        }, 1500)
      })
    },
    editData ({ id, name, description }) {
      this.selectedCategory = { name, id, description }
      this.isOpenModal = true
    }
  }
}
</script>
