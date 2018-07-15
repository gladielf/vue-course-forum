<template>
  <div class="col-full">
    <h1>Welcome to the forum</h1>
    <CategoryList :categories="categories"/>
  </div>
</template>

<script>
import sourdeData from '@/data'
import CategoryList from '@/components/CategoryList'
console.log(sourdeData)
export default {
  components: {
    CategoryList
  },
  data () {
    return {
      categories: Object.values(sourdeData.categories)
    }
  }
}
</script>
