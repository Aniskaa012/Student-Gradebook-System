import json
import csv
import os

student_data = []

def add_student():
    try:
        name = input("Enter student's name: ").strip()
        subject = input("Enter subject: ").strip()
        grade = float(input("Enter grade (0-100): "))
        if not (0 <= grade <= 100):
            raise ValueError("Grade must be between 0 and 100.")
        student_data.append({"name": name, "subject": subject, "grade": grade})
        print("✅ Student added successfully.\n")
    except ValueError as ve:
        print(f"❌ Invalid input: {ve}\n")

def calculate_average():
    if not student_data:
        print("⚠️ No student data available.\n")
        return
    total = sum(student["grade"] for student in student_data)
    avg = total / len(student_data)
    print(f"📊 Average Grade: {avg:.2f}\n")


def save_to_json(filename="students.json"):
    try:
        with open(filename, "w") as f:
            json.dump(student_data, f, indent=4)
        print(f"💾 Data saved to {filename}\n")
    except Exception as e:
        print(f"❌ Error saving to JSON: {e}\n")


def load_from_json(filename="students.json"):
    if os.path.exists(filename):
        try:
            with open(filename, "r") as f:
                global student_data
                student_data = json.load(f)
            print(f"📂 Data loaded from {filename}\n")
            print(student_data)
        except Exception as e:
            print(f"❌ Error loading JSON: {e}\n")
    else:
        print(f"⚠️ File {filename} not found.\n")


def save_to_csv(filename="students.csv"):
    try:
        with open(filename, "w", newline="") as f:
            writer = csv.DictWriter(f, fieldnames=["name", "subject", "grade"])
            writer.writeheader()
            writer.writerows(student_data)
        print(f"💾 Data saved to {filename}\n")
    except Exception as e:
        print(f"❌ Error saving to CSV: {e}\n")


def load_from_csv(filename="students.csv"):
    if os.path.exists(filename):
        try:
            with open(filename, "r") as f:
                reader = csv.DictReader(f)
                global student_data
                student_data = [dict(row) for row in reader]
                for student in student_data:
                    student["grade"] = float(student["grade"])
            print(f"📂 Data loaded from {filename}\n")
        except Exception as e:
            print(f"❌ Error loading CSV: {e}\n")
    else:
        print(f"⚠️ File {filename} not found.\n")


def main():
    while True:
        print("📘 Student Gradebook Menu:")
        print("1. Add Student")
        print("2. Calculate Average Grade")
        print("3. Save to JSON")
        print("4. Load from JSON")
        print("5. Save to CSV")
        print("6. Load from CSV")
        print("7. Exit")

        choice = input("Choose an option (1-7): ").strip()
        print()

        if choice == "1":
            add_student()
        elif choice == "2":
            calculate_average()
        elif choice == "3":
            save_to_json()
        elif choice == "4":
            load_from_json()
        elif choice == "5":
            save_to_csv()
        elif choice == "6":
            load_from_csv()
        elif choice == "7":
            print("👋 Exiting Gradebook System. Goodbye!")
            break
        else:
            print("❌ Invalid choice. Please select a number between 1 and 7.\n")

if __name__ == "__main__":
    main()
