# nuxtjs + vuex
##Some basics of using Vuex with NuxtJS (using Example)

## Nuxt Store Example (index.js)
```
export const state = () => ({
  job_ids: []
})

export const mutations = {
  STORE_JOB_IDS(state, job_ids) {
    state.job_ids = job_ids
  }
}

export const actions = {
  storeJobIds({commit}, job_ids) {
    commit('STORE_JOB_IDS', job_ids)
  }
}

export const getters = {
  getJobIds(state) {
    return state.job_ids
  }
}
```

## Nuxt Store Example (cars.js)
```
export const state = () => ({
  cars: []
})

export const mutations = {
  STORE_CARS(state, cars) {
    state.cars = cars
  }
}

export const actions = {
  storeCars({commit}, cars) {
    commit('STORE_CARS', cars)
  }
}

export const getters = {
  getCars(state) {
    return state.cars
  }
}
```

# Using Actions in Pages
## 1. Inside asyncData()
```
store.dispatch('storeJobIds', response)  // for index.js
store.dispatch('cars/storeCars', response)  // for store named cars.js
```
async asyncData({ $axios, store })

## 2. Inside Vue methods
```
this.$store.dispatch('storeJobIds', response) // for index.js
this.$store.dispatch('cars/storeCars', response) // for store named cars.js
```
# Using Getters in Pages
```
{{ $store.getters['getJobIds'] }}  // for index.js
{{ $store.getters['cars/getCars'] }}  // for store named cars.js
```
