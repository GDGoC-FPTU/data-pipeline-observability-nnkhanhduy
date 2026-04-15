# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600189
**Name:** Nguyen Ngoc Khanh Duy
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 10/10 | Kết quả chính xác, sản phẩm thực tế phù hợp với yêu cầu. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2/10 | Agent bị đánh lừa bởi dữ liệu "bẩn" có giá cực cao. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Trong thí nghiệm trên, AI Agent đã đưa ra câu trả lời sai lệnh hoàn toàn khi sử dụng bộ dữ liệu rác vì những lý do sau:
1. **Outliers (Giá trị ngoại lai):** Sản phẩm "Nuclear Reactor" được đưa vào với mức giá phi thực tế ($999,999). Vì logic của Agent được thiết kế để tìm kiếm sản phẩm "tốt nhất" dựa trên mức giá cao nhất, nó đã ngay lập tức chọn bản ghi này mà không có cơ chế kiểm tra tính hợp lý của dữ liệu.
2. **Sai kiểu dữ liệu & Null values:** Trong `garbage_data.csv`, có nhiều bản ghi thiếu thông tin hoặc sai định dạng (như giá bằng chữ). Điều này có thể gây lỗi hệ thống hoặc khiến Agent không thể truy xuất đúng thuộc tính cần thiết.
3. **Duplicate IDs:** Việc trùng lặp ID khiến quá trình indexing dữ liệu bị sai lệch, dẫn đến việc Agent có thể lấy nhầm thông tin của các sản phẩm không liên quan.

---

## 3. Ket luan

**Quality Data > Quality Prompt?**
Tôi hoàn toàn đồng ý. Thí nghiệm này chứng minh rõ ràng nguyên tắc **GIGO (Garbage In - Garbage Out)**. Cho dù câu lệnh (Prompt) của bạn có được tối ưu hóa tốt đến đâu, nếu dữ liệu đầu vào (Knowledge Base) chứa các giá trị ngoại lai hoặc dữ liệu "bẩn", Agent vẫn sẽ đưa ra những quyết định sai lầm. Do đó, việc xây dựng một Pipeline ETL mạnh mẽ để làm sạch và kiểm định dữ liệu là yếu tố sống còn cho sự ổn định của các hệ thống AI.
