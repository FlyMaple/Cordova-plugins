``` HTML
<!-- InAppBrowser -->
<button id="open_self">open_self</button>
<button id="open_blank">open_blank</button>
<button id="open_system">open_system</button>
<div class="open_message"></div>
```

``` JS
(function () {
  var url = 'https://cmsdev.aegislab.com/netgear_portal/index.html#/dashboard.html';
  var options = 'location=yes,zoom=yes,hidden=no,clearcache=no,clearsessioncache=no,hardwareback=no,mediaPlaybackRequiresUserAction=no,shouldPauseOnSuspend=no';
  var win;
  function OpenSelf() {
      win = cordova.InAppBrowser.open(url, '_self', options);
      bindWindowListener();    //  只有 InAppBrowser 才有這些事件綁訂
  }

  function OpenBlank() {
      cordova.InAppBrowser.open(url, '_blank', options);
      bindWindowListener();
  }

  function OpenSystem() {
      cordova.InAppBrowser.open(url, '_system', options);
      bindWindowListener();
  }

  function bindWindowListener() {
      win.addEventListener('loadstart', xLoadStart);
      win.addEventListener('loadstop', xLoadStop);
      win.addEventListener('loaderror', xLoadError);
      win.addEventListener('exit', xExit);
  }

  function xLoadStart() {
      alert('xLoadStart');
      navigator.notification.alert(arguments, null, 'Alert');
  }

  function xLoadStop() {
      alert('xLoadStop');
      win.insertCSS({ code: "body{background: red;" });
      win.executeScript({ code: 'alert(123);' }, exeCallback);
      // win.close();
      navigator.notification.alert(arguments, null, 'Alert');
  }

  function exeCallback() {
      jQuery('.open_message').text('callback');
  }

  function xLoadError() {
      alert('xLoadError');
      navigator.notification.alert(arguments, null, 'Alert');
  }

  function xExit() {
      alert('xExit');
      navigator.notification.alert(arguments, null, 'Alert');
  }

  /**
   *  _self: Opens in the Cordova WebView if the URL is in the white list, otherwise it opens in the InAppBrowser.
      _blank: Opens in the InAppBrowser.
      _system: Opens in the system's web browser.
   */
  jQuery('#open_self').on('click', OpenSelf);
  jQuery('#open_blank').on('click', OpenBlank);
  jQuery('#open_system').on('click', OpenSystem);
})();
```
