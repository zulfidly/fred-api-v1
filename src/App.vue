<template>
  <Container />
</template>

<script setup>
import {
  Document,
  Menu as IconMenu,
  Location,
  Setting,
} from '@element-plus/icons-vue'
import Container from '../src/components/Container.vue'
import { useFetch } from '@vueuse/core'
import { onMounted } from 'vue';





// using await (async) must be accompanied with <Suspense> at template side
//
// const { isFetching, error, data } = useFetch(
// // 'https://api.stlouisfed.org/fred/category?category_id=10&api_key=040734c7c172353e3248d5fd01746335&file_type=json'
//   '/domain/category?category_id=10&api_key=040734c7c172353e3248d5fd01746335&file_type=json'
//   )
//   console.log(data, error, isFetching);

onMounted(()=> {
  mockCategories().then((res)=> {
    const data = JSON.parse(res)
    console.log('mock', data);
  })
})

function mockCategories() {
  // main menu items for side bar
  return new Promise((resolve) => {
    setTimeout(() => {
        resolve(
            JSON.stringify(
                {
                    "categories": [
                        {
                            "id": 32991,
                            "name": "Money, Banking, & Finance",
                            "parent_id": 0
                        },
                        {
                            "id": 10,
                            "name": "Population, Employment, & Labor Markets",
                            "parent_id": 0
                        },
                        {
                            "id": 32992,
                            "name": "National Accounts",
                            "parent_id": 0
                        },
                        {
                            "id": 1,
                            "name": "Production & Business Activity",
                            "parent_id": 0
                        },
                        {
                            "id": 32455,
                            "name": "Prices",
                            "parent_id": 0
                        },
                        {
                            "id": 32263,
                            "name": "International Data",
                            "parent_id": 0
                        },
                        {
                            "id": 3008,
                            "name": "U.S. Regional Data",
                            "parent_id": 0
                        },
                        {
                            "id": 33060,
                            "name": "Academic Data",
                            "parent_id": 0
                        }
                    ]
                }
            )
        )
    }, 250)
})
}
</script>


<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
