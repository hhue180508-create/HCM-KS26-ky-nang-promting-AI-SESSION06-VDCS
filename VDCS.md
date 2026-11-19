# **BÁO CÁO: THIẾT KẾ GIẢI PHÁP PROMPTING ỨNG DỤNG AI TRONG HỌC TẬP & NGHIÊN CỨU**

## **1\. Bước 1: Thiết kế giải pháp (I/O)**

### **1.1. Mục tiêu giải pháp**

Xây dựng một hệ thống AI hỗ trợ sinh viên học tập bằng phương pháp Feynman và tự động đánh giá câu trả lời theo Rubric.

Hệ thống có hai nhiệm vụ chính:

* **Feynman Tutor:** Giải thích kiến thức đơn giản, phát hiện phần sinh viên chưa hiểu và hướng dẫn học lại.  
* **Rubric Grading:** Đánh giá câu trả lời dựa trên các tiêu chí có sẵn, chấm điểm và đưa ra nhận xét cải thiện.

### **1.2. Input (Dữ liệu đầu vào)**

| Thông tin | Nội dung |
| ----- | ----- |
| Chủ đề học tập | Kiến thức sinh viên cần tìm hiểu |
| Tài liệu tham khảo | Nội dung bài học hoặc tài liệu do sinh viên cung cấp |
| Câu trả lời | Phần giải thích kiến thức của sinh viên |
| Rubric | Các tiêu chí và thang điểm đánh giá |
| Tổng điểm | Điểm tối đa của bài đánh giá |

**Ví dụ dữ liệu đầu vào:**

* Chủ đề: Protocol trong mạng máy tính.  
* Tài liệu: Protocol là tập hợp các quy tắc giúp các thiết bị giao tiếp và trao đổi dữ liệu.  
* Câu trả lời của sinh viên: Protocol là quy tắc giúp máy tính trao đổi thông tin với nhau. Ví dụ HTTP giúp trình duyệt giao tiếp với máy chủ.  
* Rubric: Độ chính xác (4 điểm), giải thích dễ hiểu (3 điểm), ví dụ thực tế (3 điểm).  
* Tổng điểm: 10 điểm.

### **1.3. Output (Kết quả đầu ra)**

Hệ thống trả về kết quả theo cấu trúc:

1. **Phần gia sư Feynman:** Giải thích kiến thức đơn giản, chỉ ra nội dung sinh viên hiểu đúng và phần còn thiếu.  
2. **Phần đánh giá Rubric:** Bảng điểm theo từng tiêu chí, tổng điểm và nhận xét.  
3. **Phần cải thiện:** Gợi ý cách sửa câu trả lời và câu hỏi kiểm tra lại kiến thức.

---

## **2\. Bước 2: Viết Prompt hoàn chỉnh**

### **Prompt thực thi**

**Vai trò (Role):** Bạn là AI Tutor chuyên hỗ trợ học tập và đánh giá kiến thức sinh viên.

**Nhiệm vụ (Task):** Sử dụng phương pháp Feynman để giải thích kiến thức và Rubric để đánh giá câu trả lời của sinh viên.

**Dữ liệu đầu vào:**

* Chủ đề: {{CHU\_DE}}  
* Tài liệu tham khảo: {{TAI\_LIEU}}  
* Câu trả lời của sinh viên: {{CAU\_TRA\_LOI}}  
* Tiêu chí Rubric: {{RUBRIC}}  
* Tổng điểm tối đa: {{TONG\_DIEM}}

**Quy trình xử lý:**

1. Đọc và phân tích tài liệu được cung cấp.  
2. Giải thích chủ đề bằng ngôn ngữ đơn giản, dễ hiểu theo phương pháp Feynman.  
3. Đối chiếu câu trả lời của sinh viên với tài liệu và các tiêu chí Rubric.  
4. Chấm điểm từng tiêu chí, nêu rõ lý do cho điểm.  
5. Chỉ ra kiến thức còn thiếu hoặc chưa chính xác.  
6. Đề xuất cách cải thiện và đưa ra một câu hỏi để sinh viên tự kiểm tra lại kiến thức.

**Ràng buộc xử lý lỗi:**

* Nếu thiếu chủ đề hoặc câu trả lời, không tự suy đoán mà yêu cầu người dùng bổ sung.  
* Nếu thiếu tài liệu tham khảo, thông báo rằng việc kiểm tra độ chính xác sẽ bị giới hạn.  
* Nếu thiếu Rubric, yêu cầu cung cấp tiêu chí chấm điểm, không tự ý đặt ra thang điểm chính thức.  
* Nếu tổng điểm không khớp với tổng điểm các tiêu chí, thông báo lỗi và yêu cầu kiểm tra lại.  
* Nếu dữ liệu đầu vào bị sai định dạng hoặc không đọc được, yêu cầu gửi lại dữ liệu.  
* Không tự tạo thông tin hoặc trích dẫn không có trong tài liệu.  
* Chỉ đánh giá nội dung bài làm, không đánh giá người học.  
* Tổng điểm không được vượt quá điểm tối đa.

**Định dạng Output:**

Trả kết quả theo cấu trúc:

1. Giải thích kiến thức theo Feynman.  
2. Bảng đánh giá Rubric gồm: Tiêu chí, Điểm tối đa, Điểm đạt được, Nhận xét.  
3. Tổng điểm.  
4. Những điểm cần cải thiện.  
5. Câu hỏi kiểm tra lại kiến thức.

**Phong cách:** Thân thiện, dễ hiểu, khách quan, mang tính hướng dẫn và phù hợp với sinh viên.

---

## **3\. Bước 3: Chạy thử Prompt và kết quả**

### **3.1. Dữ liệu chạy thử**

* Chủ đề: Protocol trong mạng máy tính.  
* Tài liệu: Protocol là tập hợp các quy tắc giúp các thiết bị giao tiếp và trao đổi dữ liệu.  
* Câu trả lời sinh viên: "Protocol là quy tắc giúp máy tính trao đổi thông tin với nhau. Ví dụ HTTP giúp trình duyệt giao tiếp với máy chủ."  
* Rubric:  
  * Độ chính xác: 4 điểm.  
  * Giải thích dễ hiểu: 3 điểm.  
  * Ví dụ thực tế: 3 điểm.  
* Tổng điểm: 10 điểm.

### **3.2. Kết quả AI phản hồi (Output mẫu)**

**A. Giải thích theo phương pháp Feynman**

Protocol có thể hiểu là bộ quy tắc giúp các thiết bị máy tính hiểu và trao đổi thông tin với nhau.

Ví dụ: Khi bạn truy cập một website, trình duyệt sử dụng giao thức HTTP để trao đổi dữ liệu với máy chủ.

**B. Đánh giá theo Rubric**

| Tiêu chí | Điểm tối đa | Điểm đạt |
| ----- | ----- | ----- |
| Độ chính xác | 4 | 4 |
| Giải thích dễ hiểu | 3 | 3 |
| Ví dụ thực tế | 3 | 2 |
| **Tổng điểm** | **10** | **9** |

**C. Nhận xét**

* Điểm tốt: Sinh viên hiểu đúng khái niệm Protocol và giải thích ngắn gọn, dễ hiểu.  
* Điểm cần cải thiện: Ví dụ HTTP đã phù hợp nhưng chưa nói rõ HTTP là giao thức trao đổi dữ liệu giữa trình duyệt và máy chủ.

**D. Gợi ý cải thiện**

Có thể trình bày đầy đủ hơn:

"Protocol là tập hợp các quy tắc giúp các thiết bị giao tiếp và trao đổi dữ liệu với nhau. Ví dụ, HTTP là giao thức cho phép trình duyệt gửi yêu cầu và nhận dữ liệu từ máy chủ khi truy cập website."

**E. Câu hỏi kiểm tra lại**

HTTP có vai trò gì khi bạn truy cập một trang web?

---

## **4\. Kết luận**

Giải pháp kết hợp Feynman Tutor và Rubric Grading giúp sinh viên hiểu kiến thức sâu hơn, nhận biết phần còn thiếu và tự cải thiện câu trả lời. Việc sử dụng Prompt có biến số và điều kiện xử lý lỗi giúp hệ thống linh hoạt, hạn chế đánh giá sai khi dữ liệu đầu vào bị thiếu hoặc không hợp lệ.

AI chỉ đóng vai trò hỗ trợ giải thích và đánh giá ban đầu. Giảng viên vẫn cần kiểm tra và xác nhận điểm số chính thức.

