# Flight Performance Analytics & Decision Support

## Hệ thống hỗ trợ ra quyết định phân tích và dự đoán hiệu suất vận hành chuyến bay

**Portfolio định hướng IT Business Analyst · Data Warehouse · Decision Support System**

Dự án kết hợp dữ liệu lịch sử chuyến bay, kho dữ liệu và mô hình dự đoán nhằm hỗ trợ phân tích hiệu suất vận hành và xác định nhóm chuyến cần ưu tiên theo dõi. Đây là **đồ án môn học**, được thực hiện trong môi trường học thuật, chưa triển khai tại doanh nghiệp.

| Thông tin | Nội dung |
| --- | --- |
| Học phần | Kho dữ liệu và Hệ thống ra quyết định |
| Thời gian hoàn thành báo cáo | Tháng 9/2026 |
| Quy mô nhóm | 5 thành viên |
| Vai trò của tôi | Nhóm trưởng; tìm hiểu pipeline, lựa chọn công nghệ, theo dõi tổng thể dự án; phụ trách toàn bộ Chương 2 |
| Dữ liệu | BTS On-Time Performance, chuyến bay tại Hoa Kỳ giai đoạn 2021–2025 |
| Quy mô dữ liệu nguồn | 33.653.101 bản ghi |
| Nội dung repository | Báo cáo và tài liệu giới thiệu dự án |

**[Mở tài liệu báo cáo trong repository](https://github.com/tuyettranworkmail/DW_DSS/tree/main)** — tải file Word để xem đầy đủ sơ đồ, biểu đồ và kết quả thực nghiệm. Repository này phục vụ việc xem xét tài liệu; không phải bộ mã nguồn đầy đủ để cài đặt và chạy hệ thống.

## 1. Bài toán và mục tiêu nghiệp vụ

Trong bối cảnh lập kế hoạch vận hành, người điều phối cần biết hiệu suất chuyến bay biến động như thế nào và nhóm chuyến nào cần được quan tâm trước. Chỉ nhìn vào tổng số chuyến trễ chưa đủ để xác định mức độ ưu tiên theo hãng bay, sân bay hoặc thời gian.

Dự án hướng đến ba câu hỏi:

- **Hiện trạng:** Tỷ lệ trễ và hiệu suất vận hành thay đổi như thế nào theo thời gian, hãng bay và sân bay?
- **Rủi ro:** Với thông tin có trước giờ khởi hành, nhóm chuyến nào có nguy cơ đến trễ từ 15 phút trở lên?
- **Ưu tiên:** Khi nguồn lực theo dõi có giới hạn, nên rà soát nhóm chuyến nào trước?

Người dùng mục tiêu trong kịch bản của đồ án là nhân sự phân tích và điều phối vận hành. Kết quả được định hướng làm thông tin tham khảo cho việc xem xét nguồn lực; **chưa phải hệ thống tự động điều phối chuyến bay hoặc nhân sự**.

## 2. Giải pháp tổng thể của nhóm

| Thành phần | Công nghệ | Vai trò trong hệ thống |
| --- | --- | --- |
| Xử lý dữ liệu | Python, DuckDB, Parquet | Kiểm tra chất lượng, làm sạch và tổ chức dữ liệu để xử lý trên máy cá nhân |
| Dự đoán rủi ro | XGBoost | Sinh điểm rủi ro đến trễ từ 15 phút trở lên cho từng chuyến bay |
| Tích hợp và lưu trữ | SQL Server, SSIS | Tổ chức kho dữ liệu và nạp dữ liệu vào các bảng phục vụ phân tích |
| Phân tích đa chiều | SSAS Multidimensional, MDX | Phân tích theo các chiều thời gian, hãng bay và sân bay |
| Trực quan hóa | Power BI | Trình bày hiện trạng, kết quả dự đoán và góc nhìn hỗ trợ ra quyết định |

Phần xử lý dữ liệu tạo đầu vào cho kho dữ liệu và mô hình. Kết quả dự đoán được thiết kế để kết hợp với dữ liệu lịch sử, bổ sung góc nhìn rủi ro bên cạnh các chỉ số mô tả vận hành.

## 3. Đóng góp cá nhân

Tôi đảm nhiệm vai trò **nhóm trưởng**, nghiên cứu pipeline, lựa chọn công nghệ và nắm luồng xử lý tổng thể để phối hợp công việc giữa các thành viên. Phần chuyên môn tôi trực tiếp phụ trách được trình bày trong **toàn bộ Chương 2 của báo cáo**.

| Công việc tôi phụ trách | Đầu ra và giá trị đóng góp |
| --- | --- |
| Tìm hiểu dữ liệu và ý nghĩa các trường | Làm rõ nguồn dữ liệu, phạm vi sử dụng và cơ sở giữ/bỏ cột, giúp các bước xử lý bám sát ý nghĩa nghiệp vụ |
| Nghiên cứu và xây dựng pipeline xử lý bằng Python/DuckDB | Tổ chức các bước kiểm tra, làm sạch và xuất dữ liệu; xử lý dữ liệu lớn theo cách phù hợp với giới hạn bộ nhớ |
| Phân tích khám phá dữ liệu | Làm rõ mất cân bằng nhãn, dữ liệu thiếu và khác biệt tỷ lệ trễ giữa các nhóm; tạo cơ sở cho lựa chọn đặc trưng và cách đánh giá |
| Xây dựng đặc trưng và kiểm soát rò rỉ dữ liệu | Giới hạn đầu vào dự đoán ở thông tin có trước khởi hành; tách train, validation và test theo thời gian để đánh giá trên giai đoạn sau |
| Thực nghiệm, đánh giá mô hình và ngưỡng cảnh báo | So sánh bốn cấu hình XGBoost; diễn giải đánh đổi giữa phát hiện chuyến trễ, cảnh báo nhầm và khối lượng cần theo dõi |
| Dự đoán hàng loạt và tài liệu hóa kết quả | Xuất kết quả chấm điểm cho 6.879.484 chuyến hợp lệ năm 2025, tạo đầu ra phục vụ bước tích hợp tiếp theo |

**Phạm vi đóng góp:** SSIS, SSAS và dashboard Power BI được trình bày như thành phần của giải pháp chung. Tôi không quy toàn bộ sản phẩm của nhóm thành phần việc cá nhân.

## 4. Kết quả và ý nghĩa

Các số liệu dưới đây được ghi nhận trong báo cáo, không phải kết quả vận hành tại doanh nghiệp.

| Kết quả | Ý nghĩa |
| --- | --- |
| Kiểm tra dữ liệu nguồn gồm **33,65 triệu bản ghi**, giai đoạn 2021–2025 | Cho thấy khả năng tổ chức và xử lý dữ liệu vượt phạm vi bảng tính thông thường |
| Huấn luyện mô hình cuối trên **19.153.634 chuyến hợp lệ** của giai đoạn 2021–2023 | Khai thác dữ liệu lịch sử; sử dụng năm 2024 để lựa chọn cấu hình/ngưỡng và năm 2025 để kiểm tra |
| Chấm điểm **6.879.484 chuyến** trong tập test năm 2025 | Tạo đầu ra rủi ro ở quy mô lớn phục vụ phân tích tiếp theo |
| Nhóm **10% chuyến có điểm rủi ro cao nhất** có tỷ lệ trễ **40,97%**, so với mức nền **22,31%** | Tập trung được nhóm có tỷ lệ trễ cao hơn khoảng **1,84 lần**, hỗ trợ xác định thứ tự ưu tiên rà soát |

Kết quả top 10% cho thấy giá trị của **xếp hạng rủi ro**, nhưng chỉ bao phủ khoảng **18,36% tổng số chuyến thực sự trễ**. Lift 1,84 lần không có nghĩa giảm 84% số chuyến trễ hoặc tăng tương ứng hiệu quả vận hành.

Tại ngưỡng cảnh báo 0,18, mô hình đạt precision khoảng **30,34%**, recall **64,67%** và F1 **0,4130** trên test. Tỷ lệ cảnh báo nhầm còn cao, nên kết quả phù hợp để hỗ trợ rà soát kết hợp thông tin bổ sung hơn là tự động kích hoạt hành động điều chuyển nguồn lực có chi phí cao.

## 5. Bài học dưới góc nhìn Business Analyst

**Bắt đầu từ nhu cầu ra quyết định trước khi chọn dữ liệu.** Ở giai đoạn đầu, tôi tiếp cận bài toán bằng cách tìm dataset rồi mới xác định hướng thực hiện. Qua dự án, tôi nhận ra cần làm rõ người dùng, quyết định họ cần đưa ra, thời điểm quyết định và thông tin cần thiết trước khi lựa chọn dữ liệu.

**Chuyển chỉ số kỹ thuật thành ý nghĩa nghiệp vụ.** Một mô hình phát hiện được nhiều chuyến trễ vẫn có thể tạo quá nhiều cảnh báo nhầm. Khi đề xuất sử dụng kết quả, cần cân nhắc cả khả năng theo dõi, chi phí hành động và hậu quả của việc bỏ sót.

**Đánh giá đúng phạm vi giải pháp.** Mô hình dự đoán rủi ro không tự động trả lời cần bổ sung bao nhiêu nhân sự hoặc điều phối chuyến nào. Những quyết định đó còn cần quy tắc nghiệp vụ, ràng buộc nguồn lực và xác nhận từ người vận hành.

## 6. Hướng dẫn đọc báo cáo

| Nội dung cần xem | Vị trí trong báo cáo |
| --- | --- |
| Nguồn dữ liệu và cơ sở xử lý | Mục 2.1–2.2 |
| Pipeline và lựa chọn công nghệ | Mục 2.3 |
| EDA, đặc trưng, mô hình và đánh giá | Mục 2.4 |
| Dự đoán hàng loạt | Mục 2.5 |
| Kho dữ liệu, SSIS và SSAS của nhóm | Chương 3 |
| Dashboard và góc nhìn hỗ trợ ra quyết định của nhóm | Chương 4 |

**Gợi ý đọc nhanh:** xem phần đóng góp cá nhân ở trên, sau đó đọc mục **2.4.5** để hiểu kết quả và giới hạn của mô hình, cùng **2.4.6–2.5** để xem đầu ra của quy trình dự đoán.

## 7. Giới hạn và hướng phát triển

- Dữ liệu thuộc thị trường hàng không Hoa Kỳ; chưa kiểm chứng khả năng áp dụng cho Việt Nam.
- Chưa triển khai thực tế hoặc đo lường mức giảm trễ, tiết kiệm chi phí hay cải thiện năng suất vận hành.
- Độ chính xác cảnh báo và mức khớp xác suất còn hạn chế; cần bổ sung dữ liệu phù hợp, chẳng hạn thời tiết dự báo và tình trạng vận hành đã biết tại thời điểm chấm điểm.
- Bước phát triển tiếp theo là xác nhận nhu cầu với người dùng thực tế, xác định chi phí cảnh báo/bỏ sót và tiêu chí đánh giá hiệu quả trước khi thử nghiệm trong vận hành.

---

*Portfolio học thuật định hướng IT Business Analyst, thể hiện khả năng kết nối bài toán nghiệp vụ, dữ liệu, thiết kế giải pháp và đánh giá kết quả.*
