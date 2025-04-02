<!DOCTYPE html><html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Game Hỏi Đáp Về Tui</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
        }
        .question {
            font-size: 20px;
            margin-bottom: 15px;
        }
        .answer {
            display: block;
            margin: 10px auto;
            padding: 10px;
            width: 80%;
            font-size: 18px;
            cursor: pointer;
        }
        .correct {
            color: green;
            font-weight: bold;
        }
        .wrong {
            color: red;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>Game Hỏi Đáp Về Tui</h1>
    <div id="quiz-container">
        <p class="question" id="question">Loading...</p>
        <button class="answer" onclick="checkAnswer(0)"></button>
        <button class="answer" onclick="checkAnswer(1)"></button>
        <button class="answer" onclick="checkAnswer(2)"></button>
        <button class="answer" onclick="checkAnswer(3)"></button>
        <p id="result"></p>
    </div><script>
    const questions = [
        {
            question: "Tui có đẹp zai hong?",
            answers: ["Đẹp cực kỳ!", "Cũng tạm", "Không đẹp lắm", "Đẹp trong tâm hồn thôi"],
            correct: 0
        },
        {
            question: "Tui thường chơi game gì với người đẹp?",
            answers: ["Liên Quân", "PUBG", "Free Fire", "Chơi với trái tim"],
            correct: 2
        },
        {
            question: "Tui là ai trong mắt người đẹp?",
            answers: ["Chàng hoàng tử", "Thằng bạn vui tính", "Người bí ẩn", "Xì trung 1m5"],
            correct: 3
        },
        {
            question: "Món ăn mà tui thích nhất là gì?",
            answers: ["Pizza", "Mì cay", "Trà sữa", "Gà rán"],
            correct: 0
        },
        {
            question: "Bộ phim nào tui có thể xem đi xem lại mà không chán?",
            answers: ["Avengers", "Harry Potter", "Your Name", "Fast & Furious"],
            correct: 1
        }
    ];
    
    let currentQuestion = 0;
    
    function loadQuestion() {
        const q = questions[currentQuestion];
        document.getElementById("question").textContent = q.question;
        const buttons = document.querySelectorAll(".answer");
        buttons.forEach((btn, index) => {
            btn.textContent = q.answers[index];
        });
    }
    
    function checkAnswer(index) {
        const q = questions[currentQuestion];
        const result = document.getElementById("result");
        if (index === q.correct) {
            result.innerHTML = "<span class='correct'>Chúc mừng! Người đẹp hiểu tui quá!</span>";
        } else {
            result.innerHTML = "<span class='wrong'>Sai rồi... đau đớn tận cùng...</span>";
        }
        setTimeout(() => {
            result.textContent = "";
            currentQuestion = (currentQuestion + 1) % questions.length;
            loadQuestion();
        }, 2000);
    }
    
    loadQuestion();
</script>

</body>
</html>
