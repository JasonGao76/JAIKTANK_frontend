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
    
</body>

<script>

// make blank 5x5 matrix
let row = 5
let col = 5
let matrix = new Array();

for (let i = 0; i < row; i++) {
    matrix.push(new Array(col).fill(0));
}

// random value 0 to 99
matrix.forEach((row, rowIndex) => {
    row.forEach((value, colIndex) => {
        matrix[rowIndex][colIndex] = Math.floor(Math.random() * 100)
    })
})

// print matrix
matrix.forEach(row => {
    console.log(row.join(' '));
});
</script>