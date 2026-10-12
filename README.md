# Python-Project-

# Simple Student Marksheet Project

# Tuple of subjects
subjects = ("Physics", "Chemistry", "Maths")

# Dictionary to store data: { "name": [m1, m2, m3] }
students = {}

while True:
    print("\n--- MENU ---")
    print("1. Add Student")
    print("2. View Students")
    print("3. Save to File")
    print("4. Exit")

    choice = input("Enter choice (1-4): ")

    # 1. ADD STUDENT
    if choice == "1":
        name = input("Enter student name: ")

        # Taking marks one by one
        m1 = float(input("Enter Physics marks: "))
        m2 = float(input("Enter Chemistry marks: "))
        m3 = float(input("Enter Maths marks: "))

        # Storing in list, then adding to dictionary
        marks = [m1, m2, m3]
        students[name] = marks
        print("Student added!")

    # 2. VIEW STUDENTS
    elif choice == "2":
        if len(students) == 0:
            print("No students added yet!")
        else:
            for name in students:
                marks = students[name]
                total = marks[0] + marks[1] + marks[2]
                percent = total / 3

                # Finding grade
                if percent >= 75:
                    grade = "A"
                elif percent >= 50:
                    grade = "B"
                elif percent >= 35:
                    grade = "Pass"
                else:
                    grade = "Fail"

                print("\nName:", name)
                print("Marks:", marks)
                print("Total:", total, "/ 300")
                print("Percentage:", percent)
                print("Grade:", grade)

    # 3. SAVE TO FILE
    elif choice == "3":
        if len(students) == 0:
            print("No data to save!")
        else:
            file = open("report.txt", "w")

            for name in students:
                marks = students[name]
                total = marks[0] + marks[1] + marks[2]
                percent = total / 3

                file.write("Name: " + name + "\n")
                file.write("Total: " + str(total) + "\n")
                file.write("Percentage: " + str(percent) + "\n")
                file.write("--------------------\n")

            file.close()
            print("Saved to report.txt successfully!")

    # 4. EXIT
    elif choice == "4":
        print("Exiting program...")
        break

    else:
        print("Invalid choice, try again!")