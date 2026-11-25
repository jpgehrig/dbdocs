Class Name:

`src/main/webapp/listAll.html`

Github Location: [listAll.html](https://github.com/oracle/oracle-db-examples/blob/master/java/HRWebApp/src/main/webapp/listAll.html)

Description: This is the HTML page to show the results retrieved from the database.

Steps to be Performed:

Step 11: Create the title, stylesheet, and body of the HTML page

Step 12: Start the \<script\> tags and handle GET request

Step 13: Create a method processResponse() – To process the JSON response and show the results on the HTML page.

Step 11: Instructions to create title, stylesheet, and body of the HTML Page:

1\. Create the title, stylesheet, and body for the HTML page.

    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <title>List all Employees</title>

`<link rel="stylesheet" type="text/css" href="css/app.css" > ``</head> <body>`

Step 12: Instructions for Handling GET requests:

1\. Start the \<script\> tags and declare few variables for the URL and HTTPRequest.

`<script>`

`var xmlhttp = new XMLHttpRequest();`

`var url = "WebController";`

2\. Define the action when the requests are sent i.e., when the links for each one of the functionalities is selected.

    xmlhttp.onreadystatechange=function() {
         if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
           processResponse(xmlhttp.responseText);
         }
       }
    xmlhttp.open("GET", url, true);
    xmlhttp.send();

Step 13: Instructions for handling `processResponse() `requests:

1\. Create the function `processResponse()` to display JSON results on HTML page.

    function processResponse(response) {
    // Process the JSON response into an array.
    var arr = JSON.parse(response);
    var i;
    var out - "<table>";
    keys = Object.keys(arr[0]);
    //Print headers
    out += "<tr>"
    for(i = 0; i < keys.length; ++i) {
    out += "<th>"+keys [i]+"</th>"
    }
    out += "</tr>";
    // Print values
    for(j = 0; j < arr.length; j++) {
    out += "<tr>"
    for(i = 0; i < keys.length; ++i) {
    out += "<td>"+arr[j][keys[i]]+"</td>"
    }
    out += "</tr>"
    }
    out += "</table>";

` document.getElementById("id-emp").innerHTML = out;`

}

}
