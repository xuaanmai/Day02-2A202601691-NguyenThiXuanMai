# 03 — Individual Reflection Example

## Đóng góp của bản thân trong nhóm

| Hoạt động | Minh đã làm gì? | Kết quả |
|---|---|---|
| Scan cá nhân | Đưa ra nhiều candidate problems về tổng hợp thông tin, tra cứu tài liệu, báo cáo và tiếp thu tài liệu mới | Nhóm có thêm nhiều hướng để so sánh và lựa chọn candidate phù hợp |
| Problem Card | Xây dựng 3 Problem Cards với workflow, bottleneck và AI hypothesis rõ ràng | Giúp nhóm có cơ sở đánh giá actor, workflow và metric trước khi hội tụ |
| Pitch & Challenge | Trình bày vấn đề và đặt câu hỏi phản biện để kiểm tra actor, workflow và mức độ lặp lại của pain | Nhóm làm rõ hơn tính thực tế của từng candidate trước khi shortlist |
| Tổng hợp nhóm | Tổng hợp các candidate problems và ghi lại ý chính trong quá trình pitch/challenge | Nhóm có danh sách candidate thống nhất để thực hiện clustering và hội tụ |
| Candidate Proposal | Đề xuất vấn đề "Search theo từ khóa trả về nhiều tài liệu nhưng không chỉ ra chính xác điều khoản liên quan" | Candidate trở thành một phần của cluster về PolicyMate và được phát triển thành hướng giải quyết cuối cùng |
| Rule / Workflow / Agent | Tham gia thảo luận về boundary, workflow và AI intervention | Nhóm thống nhất chọn Workflow thay vì Agent vì quy trình có checkpoint và human review rõ ràng |

## Bảng dùng AI trong reflection

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì |
|---|---|---|---|---|
| Scan Problem | Nhờ AI gợi ý thêm các candidate problems từ trải nghiệm học tập và làm việc | Giúp mở rộng góc nhìn và phát hiện thêm các pain liên quan đến search, báo cáo và tiếp thu tài liệu | Gợi ý quá rộng | Chỉ giữ các vấn đề có actor, workflow và bottleneck cụ thể |
| Problem Card | Nhờ AI chuẩn hóa Problem Card và mô tả workflow | Viết workflow, bottleneck và AI hypothesis nhanh hơn | AI đôi khi mô tả impact và metric còn chung chung | Bổ sung dấu hiệu thực tế và giới hạn rõ phạm vi bài toán |
| Group Convergence | Dùng AI để tổng hợp candidate và so sánh các phương án | Dễ nhìn ra các candidate có workflow tương tự để gom nhóm | AI có xu hướng gom quá sớm khi chưa phân tích đủ boundary | Điều chỉnh lại cluster theo workflow và pain thực tế của nhóm |
| Rule / Workflow / Agent | Nhờ AI phản biện lựa chọn kiến trúc | AI giúp so sánh ưu và nhược điểm giữa Rule, Workflow và Agent | AI đề xuất agent quá sớm, như lựa chọn mặc định | Nhóm giữ Workflow vì có checkpoint rõ, dễ kiểm soát và cần human review |

## Bài học

- Một vấn đề tốt không chỉ là vấn đề phổ biến mà còn phải có actor, workflow và bottleneck rõ ràng để có thể thiết kế giải pháp AI.
- Việc tổng hợp candidate của cả nhóm giúp nhìn thấy nhiều pain thực chất là các bước trong cùng một workflow, từ đó dễ hội tụ thành một bài toán chung.
- AI hữu ích trong việc hệ thống hóa ý tưởng và phản biện, nhưng quyết định cuối cùng vẫn cần dựa trên evidence và phạm vi bài toán.
- Không phải bài toán nào cũng cần Agent. Với PolicyMate, Workflow kết hợp Rule và AI phù hợp hơn vì quy trình cố định, có checkpoint và cần người dùng kiểm tra trước khi ra quyết định.

Nếu làm lại:

```text
Tôi sẽ dành nhiều thời gian hơn để kiểm chứng evidence của candidate trước khi đưa vào shortlist, chẳng hạn phỏng vấn thêm người dùng hoặc thu thập log thực tế. Điều này sẽ giúp baseline và success metric có cơ sở hơn thay vì chỉ dựa trên trải nghiệm cá nhân.
```
