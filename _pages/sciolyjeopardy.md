---
layout: page
title: Trivia Game
permalink: /trivia/
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
    let q1 = new Jeopardy('What is H2O in daily life?', 'water', 2);
    let q2 = new Jeopardy('What is the outermost layer of the earth?', 'Crust', 1);
    let q3 = new Jeopardy('What is the hardness mineral on Mohs Hardness Scale?', 'Diamond', 2);
    let q4 = new Jeopardy('What is a reaction that loses electrons called?', 'Oxidation', 2);
    let q5 = new Jeopardy('What is the closest star to the Earth?', 'Sun', 2);
    let q6 = new Jeopardy('Who is the founder of his namesake uncertainty principle?', 'Heisenberg', 1);
    let q7 = new Jeopardy('Which number of Kepler\'s Laws states celestial bodies have elliptical orbits?', '1', 1);
    let q8 = new Jeopardy('What is the largest ocean on Earth?', 'Pacific', 1);
    let q9 = new Jeopardy('What is the coldest theoretical temperature in the universe?', 'Absolute Zero', 2);


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
                document.getElementById('answer').innerHTML = "Nice Try!";
                document.getElementById('score').innerHTML = "Your score is " + score + "/" + total;
                document.getElementById('correct').innerHTML = "Sorry, you have gotten " + correct + " questions correct out of " + count;
            }
            }
    }
</script>
<html>
    <div class="container" style="position: absolute; font-size: 40px;color: white;">
        <label for="number">How many questions do you want?</label>
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
    <li style="text-align: center; font-size: 30px;" id="question"></li>
</html>