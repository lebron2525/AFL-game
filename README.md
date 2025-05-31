# # Define team stats (numbers between 0-100)
team1 = {
    "name": "Hawks",
    "attack": 70,
    "defense": 65,
    "accuracy": 75
}

team2 = {
    "name": "Bombers",
    "attack": 68,
    "defense": 60,
    "accuracy": 70
}
import random

team1_score = 0
team2_score = 0

for quarter in range(1, 5):
    print(f"\n--- Quarter {quarter} ---")

    # Team 1's attacking turn
    team1_chances = random.randint(5, 10)
    for _ in range(team1_chances):
        attack_roll = random.randint(0, 100)
        if attack_roll < team1["attack"] - team2["defense"]:
            # Attempt a goal: 70% chance of goal, else behind
            if random.randint(0, 100) < team1["accuracy"]:
                team1_score += 6
                print(f"{team1['name']} scored a GOAL!")
            else:
                team1_score += 1
                print(f"{team1['name']} scored a behind.")

    # Team 2's attacking turn
    team2_chances = random.randint(5, 10)
    for _ in range(team2_chances):
        attack_roll = random.randint(0, 100)
        if attack_roll < team2["attack"] - team1["defense"]:
            if random.randint(0, 100) < team2["accuracy"]:
                team2_score += 6
                print(f"{team2['name']} scored a GOAL!")
            else:
                team2_score += 1
                print(f"{team2['name']} scored a behind.")
                print("\n--- Final Score ---")
print(f"{team1['name']}: {team1_score}")
print(f"{team2['name']}: {team2_score}")

if team1_score > team2_score:
    print(f"{team1['name']} WIN!")
elif team2_score > team1_score:
    print(f"{team2['name']} WIN!")
else:
    print("It's a DRAW!")