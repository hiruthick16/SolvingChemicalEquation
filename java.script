const submitButton = document.getElementById('start-button');
const feedbackContainer = document.getElementById('feedback');
const questionContainer = document.getElementById('question');
const scoreElement = document.getElementById('score');
const optionButtons = document.querySelectorAll('.option');
const startButton = document.getElementById('start-button');

let score = 0;
let currentQuestion = {};

const startGame = () => {
    score = 0;
    scoreElement.textContent = score;
    generateQuestion();
    feedbackContainer.textContent = '';
    optionButtons.forEach(button => {
        button.disabled = false;
    });
    startButton.style.display = 'none';
};

// Generate a random question with options
const generateQuestion = () => {
    // Example chemical equations and reactions
    const questions = [
        {
            question: "H₂ + O₂ → ?",
            options: ["H₂O", "O₂", "H₂O₂", "HO₂"],
            correctAnswer: "H₂O",
        },
        {
            question: "Na + Cl₂ → ?",
            options: ["NaCl", "Na₂Cl", "ClNa", "Na₂"],
            correctAnswer: "NaCl",
        },
        {
            question: "CaCO₃ → ?",
            options: ["CaO + CO₂", "Ca₂O + CO₂", "CaCO₂ + O₂", "CaO + C₂O₂"],
            correctAnswer: "CaO + CO₂",
        },
        {
            question: "2H₂O → ?",
            options: ["2H₂ + O₂", "H₂O₂ + O₂", "2H₂O₂", "H₂O + O₂"],
            correctAnswer: "2H₂ + O₂",
        },
        {
            question: "C₆H₁₂O₆ + O₂ → ?",
            options: ["CO₂ + H₂O", "CO₂ + O₂", "C₂O₂ + H₂O", "C₆H₁₂O₆"],
            correctAnswer: "CO₂ + H₂O",
        },
        {
            question: "HCl + NaOH → ?",
            options: ["NaCl + H₂O", "NaOH + HCl", "Na + H₂O", "Cl₂ + H₂O"],
            correctAnswer: "NaCl + H₂O",
        },
        {
            question: "N₂ + 3H₂ → ?",
            options: ["2NH₃", "N₃H₂", "NH₃", "H₃N"],
            correctAnswer: "2NH₃",
        },
        {
            question: "Fe + S → ?",
            options: ["FeS", "Fe₂S", "Fe₃S", "SFe"],
            correctAnswer: "FeS",
        },
        {
            question: "CH₄ + 2O₂ → ?",
            options: ["CO₂ + 2H₂O", "CO₂ + O₂", "CH₄O₂", "C₂O₂ + 2H₂O"],
            correctAnswer: "CO₂ + 2H₂O",
        },
        {
            question: "2Na + Cl₂ → ?",
            options: ["2NaCl", "NaCl", "Na₂Cl", "Cl₂Na"],
            correctAnswer: "2NaCl",
        }
    ];

    // Select a random question from the list
    const randomIndex = Math.floor(Math.random() * questions.length);
    currentQuestion = questions[randomIndex];

    questionContainer.innerHTML = <strong>Equation:</strong> ${currentQuestion.question};
    optionButtons.forEach((button, index) => {
        button.textContent = currentQuestion.options[index];
        button.disabled = false;
        button.addEventListener('click', checkAnswer);
    });

    // Wait for key press (Enter) to move to the next question
    document.addEventListener('keydown', handleKeyPress);
};

const checkAnswer = (event) => {
    const userAnswer = event.target.textContent;
    if (userAnswer === currentQuestion.correctAnswer) {
        feedbackContainer.textContent = 'Hooray! Correct Answer! 🎉';
        score += 1;  // Increase score for correct answer
        scoreElement.textContent = score;
    } else {
        feedbackContainer.textContent = Wrong answer! The correct answer was ${currentQuestion.correctAnswer}.;
    }

    // Disable the options once an answer is chosen
    optionButtons.forEach(button => {
        button.disabled = true;
    });

    // Inform the user to press "Enter" to proceed to the next question
    feedbackContainer.textContent += " Press 'Enter' to continue.";
};

// Handle key press for next question (Enter key)
const handleKeyPress = (event) => {
    if (event.key === "Enter") {
        // Remove the event listener to avoid multiple triggers
        document.removeEventListener('keydown', handleKeyPress);
        generateQuestion();
    }
};

startButton.addEventListener('click', startGame);
