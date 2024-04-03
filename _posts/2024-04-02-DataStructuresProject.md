---
layout: post
title: Data Structures Project
hide: true
description: Data Structures
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
            font-family: 'Playfair Display SC'; /* Brush Script MT is also good */
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
    </style>
</head>

<body>
    <h1 class="title">Nah, I'd <s>Win</s> Survive Covid in the 1900s</h1>
    <h2 class="regulartext">Hypothetically, if Covid existed in the 1900s around the time of the Titanic, what risk would you be at for COVID? Enter your information below and find out!</h2>
    <div class="inputs">
        <h3 class="inline">Name:</h3>
        <input type="text" class="white-input" placeholder="Type here..." id="name"><br>
    </div>
    <!-- <div class="inputs">
        <h3 class="inline">Passenger Class (1, 2, 3):</h3>
        <input type="number" min="1" step="1" max="3" class="white-input" placeholder="Type here..." id="passengerclass"><br>
    </div>
    <div class="inputs">
        <h3 class="inline">Sex (M/F):</h3>
        <input type="text" class="white-input" placeholder="Type here..." id="sex"><br>
    </div> -->
    <div class="inputs">
        <h3 class="inline">Age:</h3>
        <input type="number" min="1" step="1" max="100" class="white-input" placeholder="Type here..." id="age"><br>
    </div>
    <!-- <div class="inputs">
        <h3 class="inline">Number of siblings or spouses:</h3>
        <input type="number" min="1" step="1" max="10" class="white-input" placeholder="Type here..." id="siblingspouse"><br>
    </div> -->
    <div class="inputs">
        <h3 class="inline">Number of parents or children:</h3>
        <input type="number" min="1" step="1" max="10" class="white-input" placeholder="Type here..." id="parentchildren"><br>
    </div>
    <div class="inputs">
        <h3 class="inline">Fare:</h3>
        <input type="number" min="1" step="1" max="512" class="white-input" placeholder="Type here..." id="fare"><br>
    </div>
    <!-- <div class="inputs">
        <h3 class="inline">Embarkment port (C (Cherbourg), Q (Queenstown), S (Southampton)):</h3>
        <input type="text" class="white-input" placeholder="Type here..." id="port"><br>
    </div> -->
    <div class="inputs">
        <h3 class="inline">Alone (Y/N):</h3>
        <input type="text" class="white-input" placeholder="Type here..." id="alone"><br>
    </div>
    <button onclick="submit()">GAMBA</button><br>
    <h2 class="cursivetext"><span id="result"></span></h2>
</body>

<script>
    // stuff to handle inputs and fetch
</script>