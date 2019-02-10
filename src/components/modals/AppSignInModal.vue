<template>
  <app-modal name="signin" @before-open="loadCourses">
    <template slot="body" slot-scope="{}">
      {{ courses }}
    </template>
  </app-modal>
</template>

<script>
import axios from 'axios'
import AppModal from '@/components/AppModal'

export default {
  components: {
    AppModal
  },

  data () {
    return {
      courses: []
    }
  },

  methods: {
    async loadCourses (done) {
      let response = await axios.get('https://api.codecourse.com/api/courses')
      this.courses = response.data
      done()
    }
  }
}
</script>
