``` HTML
<div class="device">
  <div class="group available">
      <span class="label">available</span>
      <span class="value"></span>
  </div>
  <div class="group platform">
      <span class="label">platform</span>
      <span class="value"></span>
  </div>
  <div class="group version">
      <span class="label">version</span>
      <span class="value"></span>
  </div>
  <div class="group uuid">
      <span class="label">uuid</span>
      <span class="value"></span>
  </div>
  <div class="group cordova">
      <span class="label">cordova</span>
      <span class="value"></span>
  </div>
  <div class="group model">
      <span class="label">model</span>
      <span class="value"></span>
  </div>
  <div class="group manufacturer">
      <span class="label">manufacturer</span>
      <span class="value"></span>
  </div>
  <div class="group isVirtual">
      <span class="label">isVirtual</span>
      <span class="value"></span>
  </div>
  <div class="group serial">
      <span class="label">serial</span>
      <span class="value"></span>
  </div>
</div>
```

``` JS
(function () {
    // navigator.notification.alert(device, null, 'Alert', 'ok');
    jQuery('.device .available .value').text(device.available);
    jQuery('.device .platform .value').text(device.platform);
    jQuery('.device .version .value').text(device.version);
    jQuery('.device .uuid .value').text(device.uuid);
    jQuery('.device .cordova .value').text(device.cordova);
    jQuery('.device .model .value').text(device.model);
    jQuery('.device .manufacturer .value').text(device.manufacturer);
    jQuery('.device .isVirtual .value').text(device.isVirtual);
    jQuery('.device .serial .value').text(device.serial);
})();
```
