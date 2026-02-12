import random

# --- クイズデータ ---
quiz_data = {
    "かんたん": [
        ("パンダの主食は？",
         ["1. さかな", "2. たけ", "3. にく", "4. くだもの"], 2),

        ("日本の首都は？",
         ["1. 大阪", "2. 京都", "3. 東京", "4. 名古屋"], 3),
    ],

    "ふつう": [
        ("地球は太陽のまわりを何日で一周する？",
         ["1. 約100日", "2. 約365日", "3. 約200日", "4. 約30日"], 2),

        ("人間の骨の数は約いくつ？",
         ["1. 約50本", "2. 約100本", "3. 約206本", "4. 約500本"], 3),
    ],

    "むずかしい": [
        ("世界で一番深い海溝は？",
         ["1. マリアナ海溝", "2. 日本海溝", "3. トンガ海溝", "4. フィリピン海溝"], 1),

        ("光の速さは1秒間に約何km？",
         ["1. 約3万km", "2. 約30万km", "3. 約300km", "4. 約3000km"], 2),
    ]
}

# --- 問題追加機能 ---
def add_question():
    print("\n--- 新しい問題を追加 ---")
    level = input("難易度を選んでください（かんたん/ふつう/むずかしい）: ")

    if level not in quiz_data:
        print("その難易度はありません！")
        return

    question = input("問題文を入力: ")
    choices = []
    for i in range(4):
        choice = input(f"{i+1}番の選択肢: ")
        choices.append(f"{i+1}. {choice}")

    correct = int(input("正解の番号を入力（1～4）: "))

    quiz_data[level].append((question, choices, correct))
    print("✅ 追加しました！")

# --- メイン処理 ---
print("=== 豆知識クイズゲーム ===")

while True:
    print("\n1. クイズを始める")
    print("2. 問題を追加する")
    print("3. 終了")
    menu = input("番号を選んでください: ")

    if menu == "1":
        level = input("難易度を選んでください（かんたん/ふつう/むずかしい）: ")

        if level not in quiz_data:
            print("その難易度はありません！")
            continue

        questions = random.sample(quiz_data[level], len(quiz_data[level]))
        score = 0

        for i, quiz in enumerate(questions):
            print(f"\n問題 {i+1}")
            print(quiz[0])

            for choice in quiz[1]:
                print(choice)

            answer = int(input("番号で答えてください: "))

            if answer == quiz[2]:
                print("⭕ 正解！")
                score += 1
            else:
                print("❌ 不正解！")

        total = len(questions)
        percent = (score / total) * 100

        print("\n=== 結果 ===")
        print(f"正解数: {score}/{total}")
        print(f"正解率: {percent:.1f}%")

    elif menu == "2":
        add_question()

    elif menu == "3":
        print("ゲーム終了！")
        break

    else:
        print("正しい番号を選んでください。")
