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
            /* background-image: url(https://i.postimg.cc/CK6K8t0d/image.png); */
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
    <button class="button" onclick="getrate()">GAMBA</button><br>
    <h2 class="regulartext"><span id="result"></span></h2>
    <h2 class="regulartext"><span id="result2"></span></h2>
    <hr class="horizontalline">
    <h2 class="regulartext"><span id="result3"></span></h2>
</body>

<script>
    function getrate() {
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
        var url = "http://127.0.0.1:8086/api/ds/"
        var body = {
            name: name,
            socialclass: pclass,
            age: age,
            sex: sex,
            siblings: siblings,
            family: parentchildren,
            fare: fare,
            port: embarked,
            alone: alone
        }
        var requestOptions = {
            method: "POST",
            headers: {
            'Content-Type': 'application/json',
            },
            body: JSON.stringify(body),
            redirect: "follow"
        };
        fetch(url, requestOptions)
        .then(response => {
            if (response.status !== 200) {
                return;
            }
            response.json().then(data => {
                console.log("Data received")
                var survivability = data;
                var survivabilitypercent = Math.round(survivability * 100);
                var vaccinationrate = survivabilitypercent / 100
                document.getElementById("result").textContent = "Based on your information and your luck, the vaccination rate for those around you is:";
                document.getElementById("result2").textContent = vaccinationrate
            })
        })
        .catch(err => {
            console.log(err)
        }); 

        setTimeout(function() {
            getrisk()
        }, 500);
    }

    function getrisk() {
        // get values to feed into covid ml
        // random numbers (new_cases, total_cases)
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
        
        firstnumber = firstnumber * 80
        secondnumber = secondnumber * 80

        if (firstnumber > secondnumber) {
            var total_cases = firstnumber / 3;
            var new_cases = secondnumber / 3;
        }
        else {
            var new_cases = firstnumber;
            var total_cases = secondnumber;
        }

        var vaccination_rate = document.getElementById("result2").textContent
        var unprocessedrecovery_rate = vaccination_rate * 4/5 * 100
        var recovery_rate = Math.round(unprocessedrecovery_rate) / 100

        // send fetch to api to get risk
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");

        var raw = JSON.stringify({
            "new_cases": new_cases,
            "total_cases": total_cases,
            "recovery_rate": recovery_rate,
            "vaccination_rate": vaccination_rate
        });

        var requestOptions = {
            method: 'POST',
            headers: myHeaders,
            body: raw,
            redirect: 'follow'
        };

        fetch("http://127.0.0.1:8086/api/ds/risk", requestOptions)
            .then(response => response.text())
            .then(result => {
                var risk = result;
                var riskpercent = Math.round(risk * 100);
                document.getElementById('result3').textContent = "Your risk of getting COVID is " + riskpercent + "%";
                }
            )
            .catch(error => console.log('error', error));
    }
</script>