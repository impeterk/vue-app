<template>
  <div class="postDatail">
    <h1>This is a post page</h1>
    <p>Display the content of post with ID of {{ $route.params.id }} here!</p>

    <div>
      <button @click="showPostId">Show Post ID</button>
    </div>
    <div>
      <button @click="goHomeIn3Seconds">go home in 3 seconds</button>
    </div>
    <div>
      <button @click="goToFirstPost">go to first post</button>
    </div>

    <button><RouterLink to="/posts">&lt; Back</RouterLink></button>
  </div>
</template>

<script setup>
import { useRoute, useRouter } from 'vue-router'

const route = useRoute()
const router = useRouter()

const showPostId = () => {
  alert(`This ID of this post is: ${route.params.id}`)
}

const goHomeIn3Seconds = () => {
  setTimeout(() => {
    router.push({ name: 'home' })
  }, 3000)
}

const goToFirstPost = () => {
  router.push({
    name: 'postDetail',
    params: {
      id: 'id1'
    }
  })
}
</script>
