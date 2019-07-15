---
layout: post
title:      "Calling JS Functions from Rails Views"
date:       2019-07-15 01:04:15 +0000
permalink:  calling_js_functions_from_rails_views
---


A helpful way to call your front-end JS functions in a Rails backend is with the data-id property. Lets say you wanted to call a sort function. Simply add it to a button in a views file like below...

```
    <button type="button" id="js-button" data-id="<%=@project.id%>">
         Sort Activities
    </button>
```

then reference it in your JS front-end like below.

```
function attachSortListener() {
  $("#js-button").click(function(e) {
    let url = `/projects/${this.dataset.id}.json`;
    $.ajax({
      method: "GET",
      url: url
    }).success(function(response) {
      response.activities.sort(function(a, b) {
        var nameA = a.name.toUpperCase();
        var nameB = b.name.toUpperCase();
        if (nameA < nameB) {
          return -1;
        }
        if (nameA > nameB) {
          return 1;
        }
        return 0;
      });
      $("div.activities").html("");
      response.activities.forEach(function(x) {
        $("div.activities").append(`<p>${x.name}</p>`);
      });
    });
  });
}
```

