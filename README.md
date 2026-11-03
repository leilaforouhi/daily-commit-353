import random

QUESTIONS = [
    {
        "question": "What is the capital of France?",
        "options": ["Berlin", "Paris", "Rome", "Madrid"],
        "answer": "Paris"
    },
    {
        "question": "Which language is used for Python files?",
        "options": ["HTML", "CSS", "Python", "SQL"],
        "answer": "Python"
    },
    {
        "question": "How many days are in a week?",
        "options": ["5", "6", "7", "8"],
        "answer": "7"
    },
    {
        "question": "Which planet is known as the Red Planet?",
        "options": ["Earth", "Mars", "Venus", "Jupiter"],
        "answer": "Mars"
    },
    {
        "question": "What is 12 × 3?",
        "options": ["24", "30", "36", "42"],
        "answer": "36"
    }
]

def run_quiz():
    questions = random.sample(
        QUESTIONS,
        len(QUESTIONS)
    )

    score = 0

    for number, item in enumerate(questions, 1):
        print(f"\nQuestion {number}: {item['question']}")

        options = item["options"].copy()
        random.shuffle(options)

        for index, option in enumerate(options, 1):
            print(f"{index}. {option}")

        try:
            choice = int(input("Your answer: "))

            if 1 <= choice <= len(options):
                if options[choice - 1] == item["answer"]:
                    print("Correct!")
                    score += 1
                else:
                    print("Wrong!")
            else:
                print("Invalid option.")

        except ValueError:
            print("Please enter a number.")

    print(f"\nFinal score: {score}/{len(questions)}")
    print(f"Percentage: {score / len(questions) * 100:.1f}%")

if __name__ == "__main__":
    run_quiz()
