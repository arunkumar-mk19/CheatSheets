## JS Helper Functions

### 1. Generate random color code
---
A short code that returns a random hexa decimal color.

```js
Math.floor(Math.random() * 0xffffff).toString(16)
```

### 2. Display ajax request errors
---
A function to display all kinds of errors in the ajax request.

```js
function displayErrors (err) {

    if (err && (err.responseJSON || err.statusText)) {
        let errorMsg = '<ul class="text-start">';

        if (err.responseJSON) {
            if (err.responseJSON.errors) {
            
                $.each( err.responseJSON.errors, function( key, value) {
                    errorMsg += '<li class="text-danger">' + value + '</li>';
                });
            } else if (err.responseJSON.message) {
                errorMsg += '<li class="text-danger">' + err.responseJSON.message + '</li>';
            }
        }

        if(err.status == 413 && (err.statusText == 'Payload Too Large' || err.statusText == 'Content Too Large')){

            errorMsg += `<li class="text-danger">File size is larger than ${maxFileUploadSize}MB.</li>`;

        } else if(!err.responseJSON && err.status && err.statusText){

            errorMsg += `<li class="text-danger"> Error: ${err.status} - ${err.statusText} </li>`;

        }

        errorMsg += '</ul>';

        Swal.fire({
            html: errorMsg,
            icon: "error",
            title: "<h3 class='fs-1'>Error</h3>",
            width: "600",
            buttonsStyling: false,
            confirmButtonText: "Ok, got it!",
            customClass: {
                confirmButton: "btn btn-danger"
            }
        });
    }
}
```