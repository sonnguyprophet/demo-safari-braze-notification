<template>
  <Tutorial />
</template>

<script>
export default {
  mounted() {
    var init = appboy.initialize("2c2c5bf1-7c92-4cac-bb98-8dd72f4d52e5", {
      baseUrl: "sdk.iad-05.braze.com",
      safariWebsitePushId: "web.com.betprophet.co",
      enableLogging: true,
      doNotLoadFontAwesome: true
    });
    var interval;
    interval = setInterval(function() {
      console.info("Does AppBoy initialize himself? " + init);
      // When library is ready
      if (init === true) {
        clearInterval(interval);
        //$user_id - can be the same
        appboy.openSession();

        if (!appboy.isPushSupported()) {
          console.error("Push notifications are not supported by browser!");
        }

        if (appboy.isPushPermissionGranted()) {
          console.log("Push permission granted");
        } else {
          console.log("Push permission not granted");
        }

        if (!appboy.isPushBlocked()) {
          console.log(
            "Push notifications are not blocked, so lets register user on them"
          );
        }
      }
    }, 100);
  }
};
</script>
