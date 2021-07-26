# Password Generator Web Page. 
Here you fill find a password generator, you may create a randomized password using upper and lower case letters, special characters, and numbers. 


# Password Generator FINAL JAVASCRIPT CODE!
//Assignment code
// global variables
var enter;
var generateNumber;
var generateCharacter;
var generateUpperCase;
var generateLowerCase;
//password variables
character = ["!", "#", "$", "%", "&", "'", "(", ")", "*", "+", ",", "-", ".", "/", "\:", "\;", " < ", "=", " > ", " ? ", "@", "[", "\\", "]", " ^ ", "_", "`", "{", "|", "}", "~"];
number = [1, 2, 3, 4, 5, 6, 7, 8, 9];
alpha = ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"];
space = [];

var choices;
// converts letters to upper case. I found this on slack overflow
var toUpper = function (x) {
    return x.toUpperCase();
};

alpha2 = alpha.map(toUpper);

var get = document.querySelector("#generate");
get.addEventListener("click", function () {
    ps = generatePassword();
    document.getElementById("password").placeholder = ps;
});



// password function
function generatePassword() {
    // user enter input
    enter = parseInt(prompt("How many characters would you like your password? Choose between 8 and 128"));
    // if enter is empty, alert needs value.
    if (!enter) {
        alert("This needs a value");
    } else if (enter < 8 || enter > 128) {
        // if its less then 8 or greater than 128. prompt. 
        // user imput window prompts
        enter = parseInt(prompt("You must choose between 8 and 128"));

    } else {
        // Continues once user input is validated
        generateNumber = confirm("Would you like numbers in your Password?");
        generateUpperCase = confirm("Would you like to use UPPER CASE letters in Password?");
        generateLowerCase = confirm("Would you like to use lower case letters in Password?");
        generateCharacter = confirm("Would you like to use special characters in your Password?");
    };

    // else if statements.. if user selects selects no choices. alert. 
    if (!generateCharacter && !generateNumber && !generateUpperCase && !generateLowerCase) {
        choices = alert("ERROR: user did not select any Password attributes");

    }
    // else if statements for all password variables to be used
    else if (generateCharacter && generateNumber && generateUpperCase && generateCharacter) {

        choices = character.concat(number, alpha, alpha2);
    }
    // Else if for 3 variables
    else if (generateCharacter && generateNumber && generateUpperCase) {
        choices = character.concat(number, alpha2);
    }
    else if (generateCharacter && generateNumber && generateLowerCase) {
        choices = character.concat(number, alpha);
    }
    else if (generateNumber && generateLowerCase && generateUpperCase) {
        choices = number.concat(alpha, alpha2);
    }
    else if (generateCharacter && generateLowerCase && generateUpperCase) {
        choices = character.concat(alpha, alpha2);
    }
    
    // Else if for 2 variables
    else if (generateCharacter && generateNumber) {
        choices = character.concat(number);

    } else if (generateCharacter && generateLowerCase) {
        choices = character.concat(alpha);

    } else if (generateCharacter && generateUpperCase) {
        choices = character.concat(alpha2);
    }
    else if (generateLowerCase && generateNumber) {
        choices = alpha.concat(number);

    } else if (generateLowerCase && generateUpperCase) {
        choices = alpha.concat(alpha2);

    } else if (generateNumber && generateUpperCase) {
        choices = number.concat(alpha2);
    }
    // else if for 1 variable
    else if (generateCharacter) {
        choices = character;
    }
    else if (generateNumber) {
        choices = number;
    }
    else if (generateLowerCase) {
        choices = alpha;
    }
    // space variable for UPPER CASE conversion... slack overflow. 
    else if (generateUpperCase) {
        choices = space.concat(alpha2);
    };

    // password variable... array placeholder for length. 
    var password = [];

    // creates randomness for password variables in array
    for (var i = 0; i < enter; i++) {
        var pickChoices = choices[Math.floor(Math.random() * choices.length)];
        password.push(pickChoices);
    }
    // join all password variables into a string... needed some help with this. 
    var ps = password.join("");
    UserInput(ps);
    return ps;
}
// puts password into textbox.
function UserInput(ps) {
    document.getElementById("password").textContent = ps;

}
var copy = document.querySelector("#copy");
copy.addEventListener("click", function () {
    copyPassword();
});


// I had to get help from multiple sourses to complete this assigment. But all code/functions were hand written, placed, and understood by me. 
