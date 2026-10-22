# DataMar.Online-Retail
Xây dựng hệ thống giỏ hàng gợi ý dựa trên việc kết hợp 2 mô hình User-based Collaborative Filtering và Apriori
1. Mục tiêu: Phân tích dữ liệu giao dịch bán hàng trực tuyến nhằm hiểu rõ hành vi mua hàng của khách hàng, phân nhóm và đưa ra giỏ hàng gợi ý dựa theo 2 mô hình User-based Collaborative Filtering và Apriori
2. Dữ liệu:
   - Làm sạch dữ liệu: Loại bỏ các dòng dữ liệu thiếu CustomerID, Quantity ≤ 0 và UnitPrice ≤ 0; sau lọc còn 397.884 dòng giao dịch sản phẩm.
   - Phân tích mô tả: Tổng hợp số đơn và giá trị dòng mua theo tháng; xác định khách hàng xuất hiện ở cả tháng hiện tại và tháng trước; tính phần doanh thu đến từ nhóm này.
3. Phương pháp phân tích: Chia đều dữ liệu thành train 80% (318.307 dòng) và test 20% (79.577 dòng). Đối với tập train, sử dụng K-means clustering tạo ma trận khách hàng–sản phẩm, dùng User-based Collaborative Filtering kết hợp luật Apriori với trọng số alpha = 0,5. Sau đó dùng tập test để kiểm thử lại mô hình.
4. Kết quả và đề xuất:
   
4.1. Doanh thu và số đơn tăng mạnh vào giai đoạn cuối năm:

   Sau mức thấp 447.137,35 vào tháng 2/2011, tổng giá trị dòng mua tăng lên 952.838,38 trong tháng 9, 1.039.318,79 trong tháng 10 và đạt 1.161.817,38 trong tháng 11. Giá trị tháng 11 cao khoảng 2,6 lần tháng 2. Số đơn cũng tăng từ 987 đơn trong tháng 1 lên 2.657 đơn trong tháng 11.
   
   Đề xuất: Giai đoạn tháng 9–11 là thời điểm có hoạt động mua hàng cao, đáng được xem xét khi lập kế hoạch tồn kho, chiến dịch khuyến mại và năng lực xử lý đơn. Tuy nhiên, dữ liệu hiện tại chỉ cho thấy xu hướng đồng biến giữa số đơn và doanh thu; chưa đủ để kết luận nguyên nhân tăng trưởng hay tác động của chiến dịch cụ thể.
   
4.2. Khách hàng mua lặp lại đóng góp đáng kể vào doanh thu

   Theo phép tính trong notebook, doanh thu từ khách có mua ở cả tháng hiện tại và tháng liền trước chiếm 45,93%–57,27% doanh thu trong các tháng 1–11/2011; trung bình 51,92%. Tỷ lệ cao nhất là 57,27% vào tháng 6, thấp nhất là 45,93% vào tháng 4.
   
   Đề xuất: Doanh thu từ khách mua lặp lại là một nguồn đóng góp quan trọng, nên có cơ sở để thử nghiệm hoạt động giữ chân khách, nhắc mua lại hoặc gợi ý sản phẩm liên quan.
   
4.3. Hệ gợi ý sản phẩm: có độ bao phủ nhưng độ liên quan thấp

   Tập test có 1.868 khách hàng: 1.523 khách có lịch sử trong train (81,53%) và 345 khách cold-start (18,47%). Trong nhóm khách có lịch sử, 1.432 khách có sản phẩm mới để chấm điểm; 91 khách không có sản phẩm mới khác biệt so với train nên không được đưa vào nhóm đánh giá chính.
