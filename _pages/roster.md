---
layout: default
description: Testing the use of displaying frontend API
categories: [markdown, javascript]
comments: true
title: Roster
permalink: /data/roster
---

<table>
  <thead>
  <tr>
    <th>id</th>
    <th>name</th>
    <th>email</th>
    <th>phone number</th>
    <th>events</th>
    <th>graduating year</th>
  </tr>
  </thead>
  <tbody id = "result">

  </tbody>
</table>

<!-- Script is layed out in a sequence (no function) and will execute when page is loaded -->
<script>
  // prepare HTML result container for new output
  const resultContainer = document.getElementById("result");

  // prepare fetch options
  const url = "https://backend.dnhsscioly.tk/api/student/";

  const options = {
    method: 'GET', // *GET, POST, PUT, DELETE, etc.
    mode: 'cors', // no-cors, *cors, same-origin
    cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
    credentials: 'omit', // include, *same-origin, omit
    headers: {
      'Content-Type': 'application/json'
      // 'Content-Type': 'application/x-www-form-urlencoded',
    },
  };

  // fetch the API
  fetch(url, options)
    // response is a RESTful "promise" on any successful fetch
    .then(response => {
      // check for response errors
      if (response.status !== 200) {
          const errorMsg = 'Database response error: ' + response.status;
          console.log(errorMsg);
          const tr = document.createElement("tr");
          const td = document.createElement("td");
          td.innerHTML = errorMsg;
          tr.appendChild(td);
          resultContainer.appendChild(tr);
          return;
      }
      // valid response will have json data
      response.json().then(data => {


          for (const row of data) {

            const tr = document.createElement("tr");

            const id = document.createElement("td");
            const name = document.createElement("td");
            const email = document.createElement("td");
            const phone = document.createElement("td");

            const event = document.createElement("td");
            event.innerHTML = row.event;
              const event_select = document.createElement("select");
                var opt = document.createElement("option");
                opt.value = "anatomy";
                opt.innerHTML = "anatomy"
                event_select.appendChild(opt);
                event.appendChild(event_select);

              const event_button = document.createElement('button');
                event_button.innerHTML = "submit";
                event.appendChild(event_button);

              
            const graduation = document.createElement("td");
            

            id.innerHTML = row.id;
            name.innerHTML = row.name;
            email.innerHTML = row.email;
            phone.innerHTML = row.phoneNumber;
            graduation.innerHTML = row.graduatingYear;

            tr.appendChild(id);
            tr.appendChild(name);
            tr.appendChild(email);
            tr.appendChild(phone)
            tr.appendChild(event);
            tr.appendChild(graduation);

            resultContainer.appendChild(tr);
          }
      })
  })
  // catch fetch errors (ie ACCESS to server blocked)
  .catch(err => {
    console.error(err);
    const tr = document.createElement("tr");
    const td = document.createElement("td");
    td.innerHTML = err;
    tr.appendChild(td);
    resultContainer.appendChild(tr);
  });
</script>
