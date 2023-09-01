---
layout: post
title: "Harmonics and Intonation"
comments: true
description: "How do harmonics affect tuning?"
keywords: "vocevista, barbershop harmony, music theory"
---

# Intervals

On the left is an interval as if it were played on the piano (equal temperment). On the right,
is the same interval but tuned to remove the "beats" in the sound (just intonation)

### Major Third (C | E)

* Ratio: 5/4

<div style="position: relative; overflow: hidden; width: 100%; padding-top: 56.25%;">
    <video controls style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
        <source src="/assets/01-intonation/JustMajorThird.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>
<div style="margin-top: 10px;"> <!-- just a bit of space after the video --> </div>

Each sample has the tuning frequency removed. Play each sample and see if you can tell if
it is equal or justly tuned.

<details>
<summary>Audio Samples</summary>
<div id="audioContainer"> </div>
</details>

<div style="margin-top: 10px;"> <!-- just a bit of space after the video --> </div>

### Tritone (C | F#)

* Ratio: 7/5

<div style="position: relative; overflow: hidden; width: 100%; padding-top: 56.25%;">
    <video controls style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
        <source src="/assets/01-intonation/JustTritone.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>
<div style="margin-top: 10px;"> <!-- just a bit of space after the video --> </div>

### Minor Seventh (C | Bb)

* Ratio: 7/4

<div style="position: relative; overflow: hidden; width: 100%; padding-top: 56.25%;">
    <video controls style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
        <source src="/assets/01-intonation/JustMinorSeventh.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>
<div style="margin-top: 10px;"> <!-- just a bit of space after the video --> </div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    var pairings = [
        {file: "/examples/01_tuning/majorthird.mp3", type: 'equal'},
        {file: "/examples/01_tuning/justmajorthird.mp3", type: 'just'}
    ];

    var shuffled = shuffle(pairings);

    const container = document.getElementById('audioContainer');

    for (let i = 0; i < shuffled.length; i++) {
        let sample = pairings[i];

        // Start with an audio div
        const audio_div = document.createElement('div');
        const audio_heading = document.createElement('h5');
        audio_heading.innerHTML = "Example " + (i + 1);
        audio_div.appendChild(audio_heading);

        const audio = document.createElement('audio');
        audio.controls = true;
        audio.src = sample.file;
        audio.style = "margin-right: 10px;";
        audio_div.appendChild(audio);
        container.appendChild(audio_div);

        // Then add the buttons in the next div
        const curr_div = document.createElement('div');
        const equal_button = document.createElement('button');
        equal_button.innerHTML = 'Equal';
        equal_button.setAttribute("onclick", "mark(this)");
        equal_button.answer = 'correct';
        equal_button.background_color = "#007BFF";
        equal_button.color = "#FFFFFF";
        equal_button.border = "none";

        const just_button = document.createElement('button');
        just_button.innerHTML = 'Just';
        just_button.setAttribute("onclick", "mark(this)");
        just_button.answer = 'correct';

        if (sample.type == 'equal') {
            equal_button.answer = 'correct';
            just_button.answer = 'incorrect';
        } else {
            equal_button.answer = 'incorrect';
            just_button.answer = 'correct';
        }

        const spacing = document.createElement('div');
        spacing.style = "margin-top: 5px;";

        curr_div.appendChild(equal_button);
        curr_div.appendChild(just_button);
        curr_div.appendChild(spacing);
        container.appendChild(curr_div);
    }
});

function mark(button) {
    button.style.backgroundColor = '';

    if (button.answer == 'correct') {
        button.style.backgroundColor = 'green';
    } else {
        button.style.backgroundColor = 'red';
    }


}

function markIncorrect(btnId) {
    resetColors();
    const button =  document.getElementById(btnId);
    button.style.backgroundColor = 'red';
}

function resetColors() {
}

function shuffle(array) {
    let currentIndex = array.length, temporaryValue, randomIndex;

    // While there remain elements to shuffle...
    while (currentIndex !== 0) {

        // Pick a remaining element...
        randomIndex = Math.floor(Math.random() * currentIndex);
        currentIndex--;

        // And swap it with the current element.
        temporaryValue = array[currentIndex];
        array[currentIndex] = array[randomIndex];
        array[randomIndex] = temporaryValue;
    }

    return array;
}
</script>
