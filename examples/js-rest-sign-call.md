## JS/jQuery Example calling the REST Web Service

```js
function sign() {
    var url = $("http://localhost:1200/b6c9f13b-b987-43cd-ab08-3f5cb2a850d6").val();
    url += "/json/v1/sign";
    var reqdata = JSON.parse($("#reqdata").val());

    $.ajax({
        url:         url,
        type:        "POST",
        contentType: "application/json;encoding=utf-8",
        crossDomain: true,
        data:        reqdata,
        success:     success,
        error:       error
    });
}

function success(data, textStatus, jqXHR) {
    $("#respdata").val(JSON.stringify(data));
}
```
