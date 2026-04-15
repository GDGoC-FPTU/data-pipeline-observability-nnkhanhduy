[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23573959&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.duynnk@vinuni.edu.vn
**Name:** Nguyen Ngoc Khanh Duy

---

## Mo ta

Bài lab thực hiện xây dựng một Pipeline ETL tự động bằng Python để xử lý dữ liệu sản phẩm. Pipeline bao gồm các bước: trích xuất (Extract) từ JSON, kiểm định (Validate) chất lượng dữ liệu để loại bỏ các bản ghi lỗi, chuyển đổi (Transform) dữ liệu (tính giá giảm, chuẩn hóa category) và lưu trữ (Load) vào CSV. Ngoài ra, bài lab còn thực hiện Stress Test để đánh giá mức độ ảnh hưởng của dữ liệu rác (Garbage Data) đối với AI Agent.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
1. Tạo dữ liệu rác: `python generate_garbage.py`
2. Chạy mô phỏng để so sánh dữ liệu sạch vs rác: `python agent_simulation.py`

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output của pipeline
├── garbage_data.csv         # Dữ liệu lỗi cho Stress Test
├── agent_simulation.py      # Script mô phỏng AI Agent
├── experiment_report.md     # Báo cáo thí nghiệm
└── README.md                # File này
```

---

## Ket qua

- **Số lượng bản ghi xử lý:** 3 records được lưu vào `processed_data.csv`.
- **Số lượng bản ghi lỗi bị loại bỏ:** 2 records (giá âm và thiếu category).
- **Stress Test:** AI Agent đưa ra kết quả chính xác với dữ liệu sạch nhưng bị đánh lừa bởi giá trị ngoại lai (Nuclear Reactor) trong dữ liệu rác.
