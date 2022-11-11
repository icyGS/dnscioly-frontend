---
layout: default
description: Testing the use of displaying frontend API
categories: [markdown,javascript]
comments: true
permalink: /data/events
---
<h1>Event lists</h1>
<h3>B division events</h3>
<table>
  <thead>
  <tr>
    <th>id</th>
    <th>event name</th>
    <th>people</th>
  </tr>
  </thead>
  <tbody id = "div_b">

  </tbody>
</table>

<h3>C division events</h3>
<table>
  <thead>
  <tr>
    <th>id</th>
    <th>event name</th>
    <th>people</th>
  </tr>
  </thead>
  <tbody id = "div_c">

  </tbody>
</table>




<!-- Script is layed out in a sequence (no function) and will execute when page is loaded -->
<script>
  // prepare HTML result container for new output
  const resultContainerB = document.getElementById("div_b");
  const resultContainerC = document.getElementById("div_c");

  // prepare fetch options
  const url = "https://backend.dnhsscioly.tk/api/events/";

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
          resultContainerB.appendChild(tr);
          return;
      }
      // valid response will have json data
      response.json().then(data => {


          for (const row of data) {
            
            const tr = document.createElement("tr");

            const id = document.createElement("td");
            const event = document.createElement("td");
            const people = document.createElement("td");
              
            const graduation = document.createElement("td");
            let division = row.division;

            id.innerHTML = row.id;
            event.innerHTML = row.name;
            people.innerHTML = row.people;

            tr.appendChild(id);
            
            tr.appendChild(event);
            tr.appendChild(people);

            if (division.match("b")) {
              console.log(division);
              resultContainerB.appendChild(tr);
            } else {
              resultContainerC.appendChild(tr);
            }
            
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
    resultContainerB.appendChild(tr);
  });
</script>