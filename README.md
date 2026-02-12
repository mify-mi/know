print("=== 本格 性格診断アプリ ===")
print("10個の質問に直感で答えてください！\n")

leader = 0
strategist = 0
support = 0
creator = 0

questions = [
    ("Q1. 新しいことに挑戦するのは？",
     "1. ワクワクする", "2. 計画を立ててから", "3. みんなと一緒なら", "4. 気分次第"),

    ("Q2. グループ活動では？",
     "1. まとめ役", "2. 作戦担当", "3. サポート役", "4. アイデア担当"),

    ("Q3. 失敗したら？",
     "1. すぐ再挑戦", "2. 原因分析する", "3. 周りに相談", "4. 気にしない"),

    ("Q4. 好きな科目は？",
     "1. 体育", "2. 数学", "3. 国語", "4. 美術"),

    ("Q5. 決断は？",
     "1. 即決", "2. データ重視", "3. みんなの意見", "4. 直感"),

    ("Q6. 友達から言われるのは？",
     "1. 行動力ある", "2. 頭がいい", "3. 優しい", "4. 個性的"),

    ("Q7. トラブル発生！",
     "1. 仕切る", "2. 解決策を考える", "3. 仲裁する", "4. 空気を変える"),

    ("Q8. 将来は？",
     "1. 起業家", "2. 研究者", "3. 先生", "4. アーティスト"),

    ("Q9. 旅行なら？",
     "1. アクティブ旅", "2. 計画旅行", "3. みんなで楽しく", "4. 気まま旅"),

    ("Q10. 大事なのは？",
     "1. 行動力", "2. 論理", "3. 思いやり", "4. センス")
]

for q in questions:
    print("\n" + q[0])
    print(q[1])
    print(q[2])
    print(q[3])
    print(q[4])

    ans = input("番号を選んでください（1〜4）: ")

    if ans == "1":
        leader += 1
    elif ans == "2":
        strategist += 1
    elif ans == "3":
        support += 1
    elif ans == "4":
        creator += 1


total = leader + strategist + support + creator

print("\n=== 診断結果 ===")

print(f"🔥 リーダー型: {leader/total*100:.1f}%")
print(f"🧠 戦略家型: {strategist/total*100:.1f}%")
print(f"🌿 協調型: {support/total*100:.1f}%")
print(f"🎨 クリエイター型: {creator/total*100:.1f}%")


max_type = max(leader, strategist, support, creator)

if max_type == leader:
    print("\nあなたは『🔥リーダー型』！")
    print("決断力と行動力が武器。周囲を引っ張る存在です。")

elif max_type == strategist:
    print("\nあなたは『🧠戦略家型』！")
    print("分析力が高く、冷静な判断ができる頭脳派。")

elif max_type == support:
    print("\nあなたは『🌿協調型』！")
    print("思いやりがあり、周囲を支える大切な存在。")

else:
    print("\nあなたは『🎨クリエイター型』！")
    print("感性豊かで発想力が光るアイデアマン！")
