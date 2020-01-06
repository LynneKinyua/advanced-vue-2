<template>
  <section class="playground">
    <h1>We can Agree Vue is pretty amazing</h1>

    <select v-model="selectedComponent">
      <option
        v-for="(item, index) in componentList"
        :key="index"
        :value="item.component"
      >
        {{ item.label }}
      </option>
    </select>

    <hr>
    <component :is="selectedComponent"></component>
  </section>
</template>

<script>
import Button from '@/components/dynamic/Button'
import Header from '@/components/dynamic/Header'
// Comment out the line below, since we will be loading it asynchronously
// import TextInput from '@/components/dynamic/TextInput'

export default {
  name: 'Playground',
  data: function () {
    return {
      componentList: [
        { label: 'Button', component: Button },
        { label: 'Header', component: Header },
        {
          label: 'TextInput',
          // Async loading!
          component: () => import('@/components/dynamic/TextInput')
        }
      ],
      selectedComponent: null
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0 20px ;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #f73bed;
}
</style>
