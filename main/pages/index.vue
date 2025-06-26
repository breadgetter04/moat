<template>
    <div class="min-h-screen bg-gradient-to-r from-rose-100 to-teal-100 text-gray-900">

      <!-- Hero Section -->
      <section class=" px-8 py-24 md:py-24 text-center">
        <h1 class="text-5xl md:text-6xl font-bold leading-tight tracking-tight mb-6 text-gray-700">
          One Dashboard. <br/> Total Client Clarity.
        </h1>
        <p class="max-w-lg mx-auto font-medium text-black text-lg md:text-xl mb-8">
          Centralize protocols, track progress, and deliver results- all in <span class="italic">one</span> beautiful timeline.
        </p>
        <button
          class="px-12 py-6 shadow-xl bg-teal-400 text-pink-100 rounded-full font-semibold text-2xl hover:scale-110 transition">
          Try Moat Portal Free
        </button>
      </section>

      <!-- Features Section -->
      <section id="features" class="px-8 py-20 flex justify-center">
        <div class="w-full max-w-6xl p-6 bg-gray-700 mx-auto rounded-2xl shadow-2xl flex flex-col items-center">
          <h1 class="text-white text-4xl mb-10 text-center font-medium">Everything You Need.</h1>
          <div class="grid grid-cols-1 md:grid-cols-4 gap-12 text-center w-full">
            <div>
              <h3 class="text-lg font-medium mb-1 text-white">Never Miss a Session</h3>
              <p class="text-gray-300 text-sm">Clients book you easily, so you stay focused on your work.</p>
            </div>
            <div>
              <h3 class="text-lg font-medium mb-1 text-white">Keep It All In One Place</h3>
              <p class="text-gray-300 text-sm">Share files and resources without endless links.</p>
            </div>
            <div>
              <h3 class="text-lg font-medium mb-1 text-white">See the Full Picture</h3>
              <p class="text-gray-300 text-sm">Track progress, wins, and feedback in one clean view.</p>
            </div>
            <div>
              <h3 class="text-lg font-medium mb-1 text-white">Get paid, fast.</h3>
              <p class="text-gray-300 text-sm">Send branded invoices in seconds(and track payments).</p>
            </div>
          </div>
          <button
            class="px-6 py-3 shadow-xl bg-teal-400 text-pink-100 rounded-full font-semibold hover:scale-110 transition m-10">
            Save Hours
          </button>

        </div>
      </section>
      <!-- Footer -->
      <footer class="px-8 py-10 text-sm text-gray-500 text-center border-t border-gray-200">
        © 2025 Moat. Built for those who believe.
      </footer>
    </div>

</template>

<script setup>
import Appear from "~/components/Appear.vue"
</script>
