<template>
  <div class="home bg1" >
    <TopBar/>  

    <div class="flex justify-center flex flex-col justify-start items-start items-center mt-8">
      <div class="border-2 rounded-3xl p-8  space-y-8">
        <div class="lead-5">
          <h2 class="text-2xl font-bold text-start">Sign up</h2>
          <h2 class=" font-bold text-start">to get started</h2>
        </div>

        <div class="flex flex-col space-y-3">
          <input type="text" placeholder="Username" class="focus:shadow-md border p-4 outline-none rounded-xl" style="width: 450px;">
          <input type="text" placeholder="Email" class="focus:shadow-md border p-4 outline-none rounded-xl">
          <input type="password" placeholder="Password" class=" focus:shadow-md border p-4 outline-none rounded-xl">
          <input type="password" placeholder="Confirm Password" class="focus:shadow-md border p-4 outline-none rounded-xl">
        </div>

        <div class="space-x-4">
          <input type="checkbox" id="terms">
          <label for="terms">Agree to Our terms and Conditions</label>
        </div>
        <button class="p-4 w-full bg-green-600 text-white font-bold rounded-3xl">Continue</button>
        <div>
          <a href="/login">Already registered ? <strong>Log in</strong></a>
        </div>
      </div>
    </div>


  </div>
</template>

<script>
// @ is an alias to /src
import TopBar from '@/components/TopBar.vue'

export default {
  name: 'HomeView',
  components: {
    TopBar
  }
}
</script>
