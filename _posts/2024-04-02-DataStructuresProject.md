---
layout: post
title: Data Structures Project
hide: true
permalink: /datastructures
---

<head>
    <style>
        .title {
            font-size: 40px;
            font-style: italic;
            font-family: 'Blackletter';
        } 
        .regulartext {
            font-size: 20px;
            font-style: italic;
            font-family: 'Blackletter'; /* Brush Script MT is also good */
        }
        body {
            background-image: url(https://i.postimg.cc/CK6K8t0d/image.png);
            background-size: cover;
        }
        body::before {
            content: "";
            position: absolute;
            top: 0;
            left 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            z-index: -1;
        }
        .white-input {
            background-color: white;
            padding: 3px;
            border: 1px solid #ccc;
            border-radius: 5px;
            width: 30%;
            box-sizing: border-box;
        }
        .inline {
            display: inline;
        }
        .button {
            justify-content: center;
            background-color: white;
            color: black;
            padding: 15px 32px;
            text-align: center;
            font-size: 30px;
            margin: 4px 2px;
            border-radius: 10px;
        }
        .horizontalline {
            border: 3px solid black;
            margin-top: 10px;
            margin-bottom: 10px; 
        }
    </style>
</head>

<body>
    <h1 class="title">Nah, I'd <s>Win</s> Survive Covid in the 1900s</h1>
    <h2 class="regulartext">Hypothetically, if Covid existed in the 1900s around the time of the Titanic, what risk would you be at for COVID? Find out below!</h2>
    <hr class="horizontalline">
    <h2 class="regulartext">Enter your information:</h2>
    <div class="inputs">
        <h3 class="inline">Name:</h3>
        <input type="text" class="white-input" placeholder="Type here..." id="name"><br>
    </div>
    <div class="inputs">
        <h3 class="inline">Sex (M/F):</h3>
        <input type="text" class="white-input" placeholder="Type here..." id="sex"><br>
    </div>
    <div class="inputs">
        <h3 class="inline">Age:</h3>
        <input type="number" min="1" step="1" max="100" class="white-input" placeholder="Type here..." id="age"><br>
    </div>
    <div class="inputs">
        <h3 class="inline">Number of parents or children:</h3>
        <input type="number" min="1" step="1" max="10" class="white-input" placeholder="Type here..." id="parentchildren"><br>
    </div>
    <div class="inputs">
        <h3 class="inline">Alone (Y/N):</h3>
        <input type="text" class="white-input" placeholder="Type here..." id="alone"><br>
    </div>
    <div class="inputs">
        <h3 class="inline">Country of Residence (Abbreviation):</h3>
        <input type="text" class="white-input" placeholder="Type here..." id="country"><br>
    </div>
    <hr class="horizontalline">
    <h2 class="regulartext">Enter two random numbers from 1 to 100:</h2>
    <input type="number" min="1" max="100" class="white-input" placeholder="First number..." id="firstnumber"><br>
    <input type="number" min="1" max="100" class="white-input" placeholder="Second number..." id="secondnumber"><br>
    <hr class="horizontalline">
    <button class="button" onclick="submit()">GAMBA</button><br>
    <h2 class="regulartext"><span id="result"></span></h2>
</body>

<script>
    function submit() {
        // Inputs (name, sex, age, parent/children, country, alone)
        inputname = document.getElementById("name");
        name = inputname.value;

        inputsex = document.getElementById("sex");
        sex = inputsex.value;
        sex = sex.toLowerCase();

        inputage = document.getElementById("age");
        age = inputage.value;

        inputparentchildren = document.getElementById("parentchildren");
        parentchildren = inputparentchildren.value;

        inputalone = document.getElementById("alone");
        alone = inputalone.value;
        alone = alone.toLowerCase();

        inputcountry = document.getElementById("country");
        country = inputcountry.value;

        // Random numbers (class, siblings/spouse, fare, port)
        firstnumberinput = document.getElementById("firstnumber");
        secondnumberinput = document.getElementById("secondnumber");
        firstnumber = firstnumberinput.value;
        secondnumber = secondnumberinput.value;

        originalfirst = firstnumber;
        originalsecond = secondnumber;
        inputs = [firstnumber, secondnumber];
        for (let i = inputs.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [inputs[i], inputs[j]] = [inputs[j], inputs[i]];
        }
        [firstnumber, secondnumber] = inputs;

        fare = firstnumber * 11
        if (fare >= 500) {
            pclass = 1;
        }
        else if (fare >= 250 && fare < 500) {
            pclass = 2;
        }
        else {
            pclass = 3;
        }
        if (secondnumber % 3 == 0) {
            embarked = 'S';
        } 
        else if (secondnumber % 3 == 1) {
            embarked = 'C';
        }
        else {
            embarked = 'Q';
        }
        while (secondnumber > 5) {
            secondnumber = Math.round(secondnumber / 2)
        }
        siblings = secondnumber

        // Fetch API to get probability of survivability using Titanic ML
        
    }
</script>