<template>
  <div class="home">

    <header class="header">

      <div class="header__text-box">
        <h1 class="heading-primary">
          <span class="heading-primary--main">EmploYEET</span>
          <span class="heading-primary--sub">Yeet someone up, today!</span>
        </h1>
      </div>

      <a href="#scroll2" class="btn btn--blue">Find Employees</a>

    </header>

    <section id="scroll2" class="employee__box">

      <div class="employee__card-wrapper">
        <div v-for="employee in data" :key="employee.id" class="employee__card">
          <h4 class="employee__card-heading">
            {{ employee.name }}
          </h4>
          <div class="employee__card-details">
            <ul>
              <li>Username: {{ employee.username }}</li>
              <li>Email: {{ employee.email }}</li>
              <li>Phone: {{ employee.phone }}</li>
              <li>Website: {{ employee.website }}</li>
            </ul>
            <a @click="selectedEmployee = employee">view more</a>
          </div>
        </div>
      </div>
    </section>
    <Modal v-if="employeeSelected" :employee="selectedEmployee" @close="closeModal()"></Modal>
  </div>
</template>

<script>
import Modal from '@/components/Modal'

export default {
  components: {
    Modal
  },
  data() {
    return {
      data: {},
      selectedEmployee: {}
    }
  },
  computed: {
    employeeSelected() {
      if (Object.keys(this.selectedEmployee).length > 0) {
        document.body.style.overflow = 'hidden'
        return true
      } else {
        document.body.style.overflow = 'auto'
        return false
      }
    }
  },
  created() {
    this.getEmployees()
  },
  methods: {
    async getEmployees() {
      const res = await fetch('https://jsonplaceholder.typicode.com/users')
      this.data = await res.json()
    },
    closeModal() {
      this.selectedEmployee = {}
    }
  }
}
</script>

<style lang="scss">
@import "src/scss/main.scss";

</style>
