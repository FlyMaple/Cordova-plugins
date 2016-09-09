``` HTML
<div class="dialogs">
    <button id="dialog-alert">Alert</button>
    <button id="dialog-confirm">Confirm</button>
    <button id="dialog-prompt">Prompt</button>
    <button id="dialog-beep">Beep</button>
</div>
```
``` JS
(function () {
    function DialogAlert() {
        navigator.notification.alert(
            'alert',
            null,
            'Alert',
            'ok'
        );
    }
    function DialogConfirm() {
        navigator.notification.confirm(
            'confirm',
            null,
            'Confirm',
            ['ok2', 'cancel2']
        );
    }
    function DialogPrompt() {
        navigator.notification.prompt(
            'Please enter your name',  // message
            onPrompt,                  // callback to invoke
            'Registration',            // title
            ['Ok','Exit'],             // buttonLabels
            'Jane Doe'                 // defaultText
        );
    }
    function onPrompt(results) {
        alert("You selected button number " + results.buttonIndex + " and entered " + results.input1);
    }
    // function DialogBeep() {
    //     navigator.notification.beep(2);
    // }
    
    jQuery('#dialog-alert').on('click', DialogAlert);
    jQuery('#dialog-confirm').on('click', DialogConfirm);
    jQuery('#dialog-prompt').on('click', DialogPrompt);
    // jQuery('#dialog-beep').on('click', DialogBeep);
})();
```
