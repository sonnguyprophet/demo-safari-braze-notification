<!-- Please remove this file from your project -->
<template>
  <div
    class="relative flex items-top justify-center min-h-screen bg-gray-100 sm:items-center sm:pt-0"
  >
    <link
      href="https://cdn.jsdelivr.net/npm/tailwindcss@2.1.2/dist/tailwind.min.css"
      rel="stylesheet"
    />
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
      <button class="py-2 px-4 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-400 focus:ring-opacity-75" @click="testPushMessages">Test PushMessages</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    testPushMessages() {
      appboy.registerAppboyPushMessages(function() {
        appboy.logCustomEvent("send me push");
        appboy.requestImmediateDataFlush();
      });
    }
  }
};
</script>
