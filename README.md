import numpy as np

# ข้อมูลนักเรียนและคะแนน
student_data = [
    ['644244112','นายชวกร  เมืองถาวร'],
    ['644244115','นายญาณวุฒิ  บริบูรณ์'],
    ['674244101','นางสาวกนกวรรณ  พรหมเทพ'],
    ['674244102','นางสาวเกศินี  รุ่งเจริญดี'],
    ['674244103','นางสาวจิดาภา  ยิ้มย่อง'],
    ['674244104','นางสาวณาตาฌา  เรืองชัย'],
    ['674244105','นางสาวณิชนัทนท์  แสงทอง']
]

midterm = [[10],[9],[5],[10],[10],[10],[7]]
final_score = [[60],[55],[49],[70],[66],[59],[70]]

# ฟังก์ชันสำหรับคิดเกรด
def calculate_grade(total_score):
    if total_score >= 80:
        return 'A'
    elif total_score >= 75:
        return 'B+'
    elif total_score >= 70:
        return 'B'
    elif total_score >= 65:
        return 'C+'
    elif total_score >= 60:
        return 'C'
    elif total_score >= 55:
        return 'D+'
    elif total_score >= 50:
        return 'D'
    else:
        return 'E'

# แปลงข้อมูลเป็น numpy array
student_np = np.array(student_data)
midterm_np = np.array(midterm)
final_score_np = np.array(final_score)

# รวมคะแนนกลางภาคและปลายภาค
sum_scores = midterm_np + final_score_np

# คำนวณเกรด
grades = np.array([calculate_grade(score[0]) for score in sum_scores]).reshape(-1, 1)

# เพิ่มคะแนนและเกรดเข้าไปในข้อมูลนักเรียน
student_np = np.hstack((student_np, midterm_np, final_score_np, sum_scores, grades))

# แสดงผลลัพธ์
header = f"{'รหัสนักศึกษา':<12} | {'ชื่อ-นามสกุล':<30} | {'กลางภาค':<8} | {'ปลายภาค':<8} | {'รวม':<5} | {'เกรด':<5}"
print(header)
print("-" * len(header))
for student in student_np:
    print(f"{student[0]:<12} | {student[1]:<30} | {student[2]:<8} | {student[3]:<8} | {student[4]:<5} | {student[5]:<5}")
