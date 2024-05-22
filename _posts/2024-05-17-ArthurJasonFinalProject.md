---
layout: default
title: Arthur and Jason part for the Final Project
hide: true
permalink: /arthurjasonproject
---

<head>
    <style>
    </style>
</head>

<body>
    <!-- inputs for dimensions -->
    <!-- table for the matrix -->
    <div id="tablematrix"></div>
    <!-- options to sort/search matrix -->
    <button id="random" onclick="randomize(0, 99, initMatrix(10, 10))">Randomize</button>
    <button id="sortrow" onclick="sortrow()">Sort Row</button>
    <button id="sortcol" onclick="sortcol(10, 10)">Sort Column</button>
    <!-- input for value for target -->
    <button id="search" onclick="search()">Search</button>
    <input id="target">

</body>

<script>
    // constants
    
    
    

    // make blank 5x5 matrix
    function initMatrix(rowSize, colSize) {
        // let rowSize = 5;
        // let colSize = 5;
        let matrix = new Array();

        for (let i = 0; i < rowSize; i++) {
            matrix.push(new Array(colSize).fill(0));
        }
        return matrix
    }


    // randomize and update matrix
    function randomize(lowerRand, upperRand, matrix) {
        const table = document.createElement('table');
        //let lowerRand = 0
        //let upperRand = 99
        document.getElementById('tablematrix').innerHTML = "";
        matrix.forEach((row, rowIndex) => {
            const tr = document.createElement('tr');
            row.forEach((value, colIndex) => {
                const td = document.createElement('td');
                randomizedValue = lowerRand + Math.floor(Math.random() * (upperRand + 1))
                matrix[rowIndex][colIndex] = randomizedValue
                td.textContent = randomizedValue
                tr.appendChild(td);
            })
            table.appendChild(tr);
        })
        
        document.getElementById('tablematrix').appendChild(table);
    }

    // sort matrix row
    function sortrow() {
        // create an empty array to add the matrix row values in later
        var rowarray = [];

        // must let code know that tablematrix is a table so we can iterate through it
        matrix = document.querySelector('#tablematrix table');
        // matrix = document.getElementById('tablematrix');

        // for each row, store aech value, sort it numerically, and then update row with sorted values
        Array.from(matrix.rows).forEach((row, rowIndex) => {
            rowarray = Array.from(row.cells).map(cell => cell.textContent);
            rowarray.sort((a, b) => a - b); // UPDATE LATER WITH OUR SORTING, CANNOT KEEP JS BUILT IN SORT
            rowarray.forEach((value, colIndex) => {
                row.cells[colIndex].textContent = value;
            });
        })
    }

    // sort matrix col
    function sortcol(rowSize, colSize) {
        // define index limits and index
        var bottomcolindex = 0;
        var topcolindex = colSize - 1;
        var bottomrowindex = 0;
        var toprowindex = rowSize - 1;

        // define empty array to hold column values
        var colarray = [];

        // grab matrix
        matrix = document.querySelector('#tablematrix table');

        //
        for (bottomcolindex; bottomcolindex <= topcolindex; bottomcolindex++) {
            for (bottomrowindex; bottomrowindex <= toprowindex; bottomrowindex++) {
                colarray.push(matrix[bottomrowindex][bottomcolindex]) // error here, bottomcolindex not valid since matrix isnt being grabbed properly
            }
            colarray.sort((a, b) => a - b);
            for (bottomrowindex; bottomrowindex <= toprowindex; bottomrowindex++) {
                matrix[bottomrowindex][bottomcolindex] = colarray[bottomrowindex];
            }
        }

        
        // // iterate through each value with index
        // for (var i = 0; i <= topindex; i++) {
        //     Array.from(matrix.rows).forEach((row, rowIndex) => {
        //         console.log(row);
        //         console.log(rowIndex);
        //         // colarray.push() // push the value with index i to the array?
        //     })
        //     console.log("yay");
        // }
        // Array.from(matrix.rows).forEach((row, rowIndex) => {
        //     Array.from(row.cells).forEach((value, colIndex) => {
        //         colarray.push(parseInt(value.textContent));
        //         colarray.sort((a, b) => a - b);
        //         console.log(colarray);
        //     });
        // })
    }

    // search
    function search() {
        matrix = document.querySelector('#tablematrix table');
        Array.from(matrix.rows).forEach((row, rowIndex) => {
            Array.from(row.cells).forEach((value, colIndex) => {
                value.style.backgroundColor = "";
                value.style.color = "";
                if (parseInt(value.textContent, 10) === parseInt(document.getElementById("target").value, 10)) {
                    value.style.backgroundColor = "mistyrose";
                    value.style.color = "black";
                }
            })
        })
    }
    
    randomize(0, 99, initMatrix(10, 10));
</script>