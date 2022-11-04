---
toc: true
layout: post
description: Please use lowercase words in your answers. Number answers are in number form. 
categories: [markdown]
title: Cool Questions
---

<script>
    let score = 0
    let total = 0
    let count = 0
    let correct = 0
    class Jeopardy {
        constructor(question, answer, point) {
            this.question = question;
            this.answer = answer;
            this.point = point;
        }
        CheckAnswer(guess) {
            return guess === this.answer
        }
    }
    let q1 = new Jeopardy('What is the biggest planet in the solar system?', 'jupiter', 1);
    let q2 = new Jeopardy('What galaxy do we live in?', 'the milky way', 1);
    let q3 = new Jeopardy('What does DNA stand for?', 'deoxyribonucleic acid', 1);
    let q4 = new Jeopardy('How many bones are in the human body?', '206', 1);
    let q5 = new Jeopardy('What is the closest planet to the Earth? (on average)', 'mercury', 1);
    let q6 = new Jeopardy('Which is the main gas that makes up the atmosphere in the Earth?', 'nitrogen', 1);
    let q7 = new Jeopardy('At what temperature are Celsius and Fahrenheit equal?', '40', 1);
    let q8 = new Jeopardy('What is the largest ocean on Earth?', 'pacific', 1);
    let q9 = new Jeopardy('How many teeth does an adult human have?', '32',1);


    const qarray = [q1, q2, q3, q4, q5, q6, q7, q8, q9]
    function QNA(number) {
        for (let i = 0; i < number; i++) {
            const randomValue = qarray[Math.floor(Math.random() * qarray.length)];
            var index = qarray.indexOf(randomValue);
            if (index > -1) {
                qarray.splice(index, 1);
            }
            let guess = prompt(randomValue.question + " Points: " + randomValue.point);
            count = count + 1
            total = total + randomValue.point
            if (randomValue.CheckAnswer(guess)) {
                score = score + randomValue.point;
                correct = correct + 1
                document.getElementById('answer').innerHTML = "Well Done!";
                document.getElementById('score').innerHTML = "Your score is " + score + "/" + total;
                document.getElementById('correct').innerHTML = "You got " + correct + " questions correct out of " + count;
            }
            else {
                document.getElementById('answer').innerHTML = "You Stink!";
                document.getElementById('score').innerHTML = "Your score is " + score + "/" + total;
                document.getElementById('correct').innerHTML = "Sorry, you have gotten " + correct + " questions correct out of " + count;
            }
            }
    }
</script>
<html>
    <div class="container" style="position: absolute; font-size: 40px;color: white">
        <label for="number">How many questions do you want? (max = 9)</label>
        <br>
        <input id="number" type="number"/>
        <button onclick="QNA(document.getElementById('number').value)">Submit</button>
    </div>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <p style="text-align: center; font-size: 30px;" id="answer"></p>
    <p style="text-align: center; font-size: 30px;" id="score"></p>
    <p style="text-align: center; font-size: 30px;" id="correct"></p>
</html>