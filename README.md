# finalprepbot.py

import random

class FinalPrepBot:
    def __init__(self):
        self.topics = {
            "meiosis": {
                "What is meiosis?": "A type of cell division that produces four haploid cells (gametes).",
                "What happens in Prophase I?": "Homologous chromosomes pair up and crossing over occurs.",
                "Why is meiosis important?": "It creates genetic diversity and maintains chromosome number across generations."
            },
            "evolution": {
                "Who developed the theory of natural selection?": "Charles Darwin.",
                "What is natural selection?": "The process where organisms better adapted to the environment survive and reproduce.",
                "What is a mutation?": "A random change in DNA that can lead to variation."
            }
        }

    def start(self):
        print("📚 Welcome to FinalPrepBot – Your Study Partner!")
        while True:
            print("\nChoose a topic (meiosis, evolution) or type 'quiz', 'flashcards', or 'exit':")
            choice = input("You: ").strip().lower()

            if choice == "exit":
                print("Good luck on your finals! 👋")
                break
            elif choice in self.topics:
                self.study_topic(choice)
            elif choice == "flashcards":
                self.flashcards()
            elif choice == "quiz":
                self.quiz()
            else:
                print("Sorry, I didn't understand that. Try again.")

    def study_topic(self, topic):
        print(f"\n🧠 Studying: {topic.capitalize()}")
        for q, a in self.topics[topic].items():
            print(f"\nQ: {q}\nA: {a}")

    def flashcards(self):
        all_cards = [(q, a) for topic in self.topics.values() for q, a in topic.items()]
        random.shuffle(all_cards)
        print("\n🔁 Flashcard Mode: Press Enter to flip, type 'stop' to end.")
        for q, a in all_cards:
            print(f"\nQ: {q}")
            if input() == "stop":
                break
            print(f"A: {a}")

    def quiz(self):
        all_questions = [(q, a) for topic in self.topics.values() for q, a in topic.items()]
        random.shuffle(all_questions)
        score = 0
        print("\n📝 Quiz Mode: Type your answer or 'skip' to pass.")
        for q, a in all_questions[:5]:
            print(f"\nQ: {q}")
            ans = input("Your answer: ").strip().lower()
            if ans == "skip":
                continue
            elif ans in a.lower():
                print("✅ Correct!")
                score += 1
            else:
                print(f"❌ Incorrect. Answer: {a}")
        print(f"\n🎯 Final Score: {score}/5")

if __name__ == "__main__":
    bot = FinalPrepBot()
    bot.start()
