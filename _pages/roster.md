---
layout: page
title: Roster
permalink: /roster/
---

<head>
    Student Roster
</head>

<table>
    <thead>
    <tr>
        <th>Student</th>
        <th>Grade</th>
        <th>Email</th>
        <th>Phone Number</th>
    </tr>
    </thead>
</table>
<script>
    fetch("https://http://backend.dnhsscioly.tk/api/student/")
        .then((response) => response.json())
        .then((data) => {
        })
        .catch((err) => console.log(err));
</script>