# GPA Calculator

This repository contains a GPA calculator web application built using HTML, CSS, and JavaScript. The application allows users to calculate their GPA by selecting subjects, grades, and credits, and provides the option to print the results.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Code Overview](#code-overview)
- [Contributing](#contributing)
- [License](#license)

## Features

- Select subjects from a predefined list
- Choose grades and corresponding credits
- Calculate GPA
- Add and remove subjects dynamically
- Print GPA report

## Installation

### Prerequisites

- A web browser

### Steps

1. **Clone the Repository**

   ```sh
   git clone https://github.com/ahiru60/GPA_cal.git
   cd GPA_cal
   ```

2. **Open the Application**

   Open the `index.html` file in your web browser.

## Usage

1. **Open the Application**

   - Open `index.html` in your browser.

2. **Add Subjects**

   - Select a subject, grade, and credit from the dropdowns and click "Add".

3. **Calculate GPA**

   - Click "Calculate GPA" to see your GPA.

4. **Print Report**

   - Click "Print" to print your GPA report.

## Code Overview

### `index.html`

The main HTML file containing the structure of the GPA calculator.

```html
<!DOCTYPE html>
<html>
<head>
    <title>GPA calculator</title>
    <link href="styles.css" rel="stylesheet">
</head>
<body>
    <div id="inter">
        <div id="h1"><h1>GPA Calculator</h1></div><br><hr class="solid">
        <p id="up"></p>
        <div id="inter-inputs">
            Subject: <select name="cradit" id="credit">
                <option value="3">IT11013 : IT and Computing Fundamentals</option>
                <option value="3">IT11023 : Programming Fundamentals</option>
                <option value="3">IT11033 : Discrete Mathematics</option>
                <option value="1">IT11041 : Psychology</option>
                <option value="2">IT11052 : Leadership and Communication Skills</option>
                <option value="3">BMG11073 : Entreprenureship and Growing Business</option>
                <option value="2">IT12012 : Computer Organization & Architecture</option>
                <option value="3">IT12023 : Information Management</option>
                <option value="3">IT12063 : Data Structure and Algorithems I</option>
                <option value="3">IT12043 : Integrative Programming & Technologies</option>
                <option value="2">IT12052 : Emerging Technologies</option>
                <option value="1">IT12031 : Seminar I</option>
                <option value="3">IT21053 : Object Oriented Programming</option>
                <option value="2">IT21012 : Social and Professional Issues</option>
                <option value="2">IT21022 : Data Communication</option>
                <option value="2">IT21032 : Software Design and Implementation</option>
                <option value="3">IT21043 : Software Construction Technologies</option>
                <option value="3">IT21063 : Data Structure and Algorithems II</option>
                <option value="2">IT21072 : System Analysis and Design</option>
        </select>
        
        Grade: <select name="grade" id="grade">
            <option value="4">A+</option>
            <option value="4">A</option>
            <option value="3.7">A-</option>
            <option value="3.3">B+</option>
            <option value="3">B</option>
            <option value="2.7">B-</option>
            <option value="2.3">C+</option>
            <option value="2">C</option>
            <option value="1.7">C-</option>
            <option value="1.3">D+</option>
            <option value="1">D</option>
            <option value="0">F</option>
        </select>
        <button onclick="sum()">Add</button>
    </div> 
    </div>
    <div id="table-space">
        <table id="subTable"></table>
    </div>
    <br>
    <div id="inter-bottom">
        <div><p id="gpa"></p></div>
        <button onclick="removeRow()">Remove</button>
        <button onclick="calc()">Calculate GPA</button>
        <button onclick="reset()">Reset</button>
        <button onclick="fnExcelReport()" id="print">Print</button>
    </div>
</body>
<script>
// JavaScript functions to add, remove, calculate, and print GPA details
</script>
</html>
```

### `styles.css`

The main CSS file for styling the GPA calculator.

```css
body {
    font-family: Arial, sans-serif;
    font-size: 16px;
    color: #333;
    background-color: #e7ebf4;
}

h1 {
    font-size: 66px;
    margin: 0;
}

#h1 {
    text-align: center;
    margin-top: 30px;
    margin-bottom: 0px;
}

#inter {
    margin: 20px 0;
    margin-top: 0px;
    padding: 20px;
    padding-top: 1px;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

#inter select {
    font-size: 16px;
    padding: 6px 8px;
    border-radius: 4px;
    border: 1px solid #ccc;
    margin-right: 10px;
}

#inter button {
    font-size: 16px;
    padding: 6px 12px;
    border-radius: 4px;
    border: none;
    background-color: #576c9e;
    color: #fff;
    cursor: pointer;
    transition: all 0.2s ease-in-out;
}

#inter button:hover {
    background-color: #3e5a9c;
}

#inter button:active {
    background-color: #7a90c4;
    transform: translateY(2px);
}

#table-space {
    margin: 20px 0;
    height: 300px;
    overflow: hidden;
    overflow-y: scroll;
}

#subTable {
    width: 100%;
    border-collapse: collapse;
}

#subTable th,
#subTable td {
    padding: 8px;
    text-align: left;
    border-bottom: 1px solid rgb(203, 215, 243);
}

#subTable th {
    background-color: #f2f2f2;
    font-weight: bold;
}

#headTable th {
    background-color: #f2f2f2;
    font-weight: bold;
}

#inter-bottom {
    margin-top: 20px;
    text-align: center;
}

#inter-bottom button {
    font-size: 16px;
    padding: 6px 12px;
    border-radius: 4px;
    border: none;
    background-color: #576c9e;
    color: #fff;
    cursor: pointer;
    transition: all 0.2s ease-in-out;
}

#inter-bottom button:hover {
    background-color: #3e5a9c;
}

#inter-bottom button:active {
    background-color: #7a90c4;
    transform: translateY(2px);
}

#gpa {
    font-size: 30px;
    margin-top: 0px;
    font-weight: bold;
    height: 15px;
}

#inter-inputs {
    width: 50%;
    margin-left: auto;
    margin-right: auto;
}
```

### Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### License

This project is licensed under the [MIT License](LICENSE).
