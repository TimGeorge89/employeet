<template>
  <div class="modal">
    <div class="modal__background"></div>
    <div class="modal__card-wrapper">
      <div class="modal__card">
        <h4 class="modal__card-heading">
          {{ employee.name }}
        </h4>
        <div class="modal__card-details">
          <ul>
            <li>Username: {{ employee.username }}</li>
            <li>Email: {{ employee.email }}</li>
            <li>Address:
               {{ employee.address.street }},
               {{ employee.address.suite }},
               {{ employee.address.city }},
               {{ employee.address.zipcode }}
            </li>
            <li>Phone: {{ employee.phone }}</li>
            <li>Website: {{ employee.website }}</li>
            <li>Company: {{ employee.company.name }} <br>
                "{{ employee.company.catchPhrase }}"
            </li>
          </ul>
          <a @click="modalClose">Exit</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['employee'],
  data() {
    return {

    }
  },
  methods: {
    modalClose() {
      this.$emit('close')
    }
  }
}
</script>

<style lang="scss">



</style>
